# SwiftUI Toast message (demo):

This toast message is presented from top.

1. To change the way of presentation from bottom, move the spacer() at top in VStack in mainToastView() ViewBuilder
2. and Change to .transition(.move(edge: .bottom)) like this:

```swift
 @ViewBuilder func mainToastView() -> some View {
    if let toast = toast {
      VStack {
        Spacer()  // Move this spacer here
        ToastView(
          style: toast.style,
          message: toast.message,
          width: toast.width
        ) {
          dismissToast()
        }
      }
      .transition(.move(edge: .bottom))  // Change the direction of the transition from bottom
      .transition(AnyTransition.opacity.animation(.linear))
      .transition(AnyTransition.scale.animation(.linear))
      .transition(AnyTransition.opacity.animation(.easeInOut(duration: 0.1)))
    }
  }

```

  3. Lastly, change the sign of the offset in the ZStack:

```swift
ZStack {
  mainToastView()
    .offset(y: -32)
}.animation(.spring(), value: toast)

```

Thank you!
