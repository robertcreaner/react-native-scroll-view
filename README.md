# react-native-scroll-view
A react-native component for android that mimics the react-native iOS `ScrollView`.

- android: **ZOOM and SCROLL** content easily *(isn't supported by the react-native `ScrollView`)*.
- iOS: exports the react-native `ScrollView` *(does nothing!)*

Refer to the react-native `ScrollView` [documentation](https://facebook.github.io/react-native/docs/scrollview#props).

## Installation
```
npm install --save @ShaMan123/react-native-scroll-view
```
OR
```
yarn add @ShaMan123/react-native-scroll-view
```

## Usage

```
import ScrollView from 'react-native-scroll-view';

<ScrollView
  ref={ref => this.ref = ref}
  minimumZoomScale={0.75}
  maximumZoomScale={3}
  zoomScale={1.5}
>
  {...contentToRender}
</ScrollView>

zoomToRect() {
  this.ref.getScrollResponder().scrollResponderZoomTo({ x: 0, y: 0, width: 100, height: 100});
}

setOverScroll() {
  this.ref.getScrollResponder()
    .scrollResponderScrollNativeHandleToKeyboard(React.findNodeHandle(this.ref), 100);
}
```

## Props
| Prop  | Status | Description |
| :------------ |:---------------|:---------------| 
|...ViewProps|   ✅     | see [docs](https://facebook.github.io/react-native/docs/view#props)|
|  alwaysBounceVertical | :x:  |   |
|  contentContainerStyle | ✅  |   |
|  keyboardDismissMode |  :x: |   |
|  keyboardShouldPersistTaps |  :x: |   |
|  onContentSizeChange | ✅  |   |
|  onMomentumScrollBegin |  ✅ |   |
| onMomentumScrollEnd  | ✅  |   |
|  onScroll |  ✅ |   |
|  onScrollBeginDrag |  ✅ |   |
|  onScrollEndDrag | ✅  |   |
|  pagingEnabled | :x:  |   |
|  refreshControl | :x:  |   |
|  removeClippedSubviews | :x:  |   |
|  scrollEnabled | ✅   |   |
| showsHorizontalScrollIndicator  |  ✅  |   |
|  showsVerticalScrollIndicator |  ✅  |   |
| stickyHeaderIndices | :x:  |   |
| endFillColor | :x:  |   |
| overScrollMode | :x:  |   |
| scrollPerfTag | :x:  |   |
| DEPRECATED_sendUpdatedChildFrames | :x:  |   |
| alwaysBounceHorizontal | :x:  |   |
| horizontal | :x:  |   |
| automaticallyAdjustContentInsets | :x:  |   |
|  bounces |   ✅ |   |
|  bouncesZoom |  :x: |   |
|  canCancelContentTouches | :x:  |   |
|  centerContent |  ✅  |   |
|  contentInset |  ✅  |   |
| contentInsetAdjustmentBehavior  | :x:  |   |
| contentOffset |  ✅  |   |
| decelerationRate |  ✅  |   |
| directionalLockEnabled |  ✅  |   |
| indicatorStyle  |  ✅  | differs from the *iOS* prop, accepts a style object  |
| maximumZoomScale |  ✅  |   |
| minimumZoomScale |  ✅  |   |
| pinchGestureEnabled |  ✅  |   |
| scrollEventThrottle  | :x:  |   |
| scrollIndicatorInsets  | :x:  | pass insets through *indicatorStyle*   |
| scrollsToTop  | :x:  |   |
| snapToAlignment  | :x:  |   |
| snapToInterval  | :x:  |   |
| zoomScale |  ✅  |   |
| nestedScrollEnabled  | :x:  |   |


## Methods
| Method  | Description |
| :------------ |:---------------| 
| `scrollTo({ x, y, animated?, scale?, overScroll?, callback?})` | see `ScrollView`'s [scrollTo](https://facebook.github.io/react-native/docs/scrollview#scrollto). Added optional arguments: `scale`, `overScroll`: *`true` \| `false` \| `{ x, y }`*, `callback` |
| `scrollToEnd({ animated?, callback?})` | see `ScrollView`'s [scrollTo](https://facebook.github.io/react-native/docs/scrollview#scrolltoend). Added optional arguments: `callback` |
| `scrollResponderZoomTo({ x, y, width, height, animated?, callback?})` |  see [issue](https://github.com/facebook/react-native/issues/9830). Added optional arguments: `callback`|
| `flashScrollIndicators()` |  see `ScrollView`'s [flashScrollIndicators](https://facebook.github.io/react-native/docs/scrollview#flashscrollindicators) |
| `scrollResponderScrollNativeHandleToKeyboard(reactNode?, extraHeight, preventNegativeScrollOffset?)` |  see [issue](https://github.com/facebook/react-native/issues/3195)  |
| `getNode()` |  the same as `findNodeHandle(componentRef)`  |
| `getScrollResponder()` |  a dummy method pointing back to the component, used for chaining, enables cross platform compatibility  |
| `getScrollRef()` |  a dummy method pointing back to the component, used for chaining, enables cross platform compatibility  |

## Customizing the Gesture Responder

Pass `onStartShouldSetResponder`, `onStartShouldSetResponderCapture`, `onMoveShouldSetResponder`, `onMoveShouldSetResponderCapture` to customize the *`ScrollView`'s* behavior.

[Gesture Responder System documentation](https://facebook.github.io/react-native/docs/gesture-responder-system)
