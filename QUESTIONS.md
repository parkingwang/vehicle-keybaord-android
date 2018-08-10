常见问题列表
====

- 输入框不显示

见 README 第 4.5.1 节。
>#### 4.5.1 InputView的样式选项
**注意**
最新版本需要配置 `InputView` 的 `style`。配置方法有以下两种：
在布局文件中为 `InputView` 添加以下属性：
>
```
    style="@style/PWKInputViewStyle"
```
或者是在 `Application` 或 `Activity` 所配置的 `theme` 的 `style` 中添加配置（参考 demo 项目）：
>
```
    <item name="pwkInputStyle">@style/PWKInputViewStyle</item>
```

--
- 如何监听车牌输入或确定按钮事件

>```java
public interface OnInputChangedListener {
    /**
     * 当输入框的车牌号码发生变化时，回调此方法。
     *
     * @param number      当前输入框的车牌号码
     * @param isCompleted 当前的车牌号码是否已输入完成
     */
    void onChanged(String number, boolean isCompleted);
>  
    /**
     * 当车牌号码被输入完成后，调用此方法。
     * @param number 完整输入的车牌号码
     * @param isAutoCompleted 当前的输入完成状态，是否属于自动完成。
     *                        输入完成状态有两种：
     *                          1. 从部分车牌一直输入，直到输完最后一位时，会触发自动完成回调。此时isAutoCompleted为True。
     *                          2. 通过点击“确定”按键来触发输入完成。此时isAutoCompleted为False。
     */
    void onCompleted(String number, boolean isAutoCompleted);
}
```

--
- 如何实现长按粘贴的功能？

>目前还没有实现这一功能。可以自己继承一下InputView，重写 setOnLongClickListener，把长按监听派发给每一个子View。然后外部调用该方法，设置读取粘贴板并更新车牌。