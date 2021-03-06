## BottomNavigationViewEx ##
一个增强BottomNavigationView的安卓库。

![MIT License](https://img.shields.io/github/license/mashape/apistatus.svg) ![api 9+](https://img.shields.io/badge/API-9%2B-green.svg)
 感谢
 原项目: https://github.com/ittianyu/BottomNavigationViewEx.git

## 功能 ##

|methods|description
|---|---|
|enableAnimation|开启或关闭点击动画(文字放大效果和图片移动效果)。 默认为 true.
|enableItemShiftingMode|开始或关闭子菜单位移模式。 如果为 true，除了当前选中项，其他项的文本将会隐藏。 当菜单数大于3时，默认为 true。
|enableShiftingMode|开始或关闭导航条位移模式。如果为 true，选中项和其他项的宽度不一样。当菜单数大于3时，默认为 true。
|getBottomNavigationItemView|获取位于 position 的私有成员变量 mButton。
|getBottomNavigationItemViews|获取私有成员变量 mButtons。
|getCurrentItem|获取当前选中项的索引。
|getIconAt|获取位于 position 的图片。
|getItemCount|获取子项个数。
|getItemHeight|获取菜单高度。
|getLargeLabelAt|获取位于 position 的大标签. 每个子项包含两个标签，一个大的，一个小的。
|getSmallLabelAt|获取位于 position 的小标签. 每个子项包含两个标签，一个大的，一个小的。
|getMenuItemPosition|获取子菜单的索引。如果找不到，返回 -1。
|getOnNavigationItemSelectedListener|获取 OnNavigationItemSelectedListener。
|setCurrentItem|设置当前选中项。
|setIconMarginTop|设置 icon 的 MarginTop，用于调节图标垂直位置。
|setIconSize|设置所有的子项图标大小。
|setIconSizeAt|设置位于 position 的图标的大小。
|setIconsMarginTop|设置所有 icon 的 MarginTop，用于调节图标垂直位置。
|setIconTintList| 设置图片的渲染颜色列表(Selector)
|setIconVisibility|设置图片可见性。
|setItemBackground| 设置子项的背景。
|setItemHeight|设置子项高度。
|setLargeTextSize|设置所有子项的大标签文本大小。每个子项有两个标签，一个大的，一个小的。当子项未选中时，显示小标签；选中时，显示大标签。
|setSmallTextSize|设置所有子项的小标签文本大小。每个子项有两个标签，一个大的，一个小的。当子项未选中时，显示小标签；选中时，显示大标签。
|setTextSize|设置所有子项的大和小标签文本大小。
|setTextTintList|设置子项 TextView 的颜色。
|setTextVisibility|设置文本可见性。
|setTypeface|设置所有子项的 TextView 字体
|setupWithViewPager|和 ViewPager 绑定，当 任何一个选中项改变时，都会自动改变另一项。


## 例子 ##

**样式**

![](/read_me_images/normal.gif)

![](/read_me_images/no_animation.gif)

![](/read_me_images/no_shifting_mode.gif)

![](/read_me_images/no_item_shifting_mode.gif)

![](/read_me_images/no_text.gif)

![](/read_me_images/no_icon.gif)

![](/read_me_images/no_animation_shifting_mode.gif)

![](/read_me_images/no_animation_item_shifting_mode.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode.gif)

![](/read_me_images/no_shifting_mode_item_shifting_mode_text.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode_text.gif)

![](/read_me_images/no_shifting_mode_item_shifting_mode_and_icon.gif)

![](/read_me_images/no_item_shifting_mode_icon.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode_icon.gif)

**注意：这个 style 在安卓 4.x 上有 bug**

![](/read_me_images/with_padding.jpg)

![](/read_me_images/center_icon_only.jpg)

![](/read_me_images/smaller_text.jpg)

![](/read_me_images/bigger_icon.jpg)

![](/read_me_images/custom_typeface.jpg)

![](/read_me_images/icon_selector_1.jpg) ![](/read_me_images/icon_selector_2.jpg)

![](/read_me_images/icon_margin_top.jpg)

![](/read_me_images/unchecked_first_time.jpg)

**和 ViewPager 一起使用**

![](/read_me_images/with_view_pager.gif)

**带数字的小红圈**

![](/read_me_images/view_badger.gif)


**中间悬浮按钮**

![](/read_me_images/center_fab.jpg)


## 开始使用 ##


在 `xml` 布局中添加自定义控件:
```xml
<com.ittianyu.bottomnavigationviewex.BottomNavigationViewEx
    android:id="@+id/bnve"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_alignParentBottom="true"
    android:background="@color/colorPrimary"
    app:itemIconTint="@color/selector_item_color"
    app:itemTextColor="@color/selector_item_color"
    app:menu="@menu/menu_navigation_with_view_pager" />
```

在 `Activity` 中绑定控件:
```java
BottomNavigationViewEx bnve = (BottomNavigationViewEx) findViewById(R.id.bnve);
```

#### 禁止所有动画效果 ####
```java
bnve.enableAnimation(false);
bnve.enableShiftingMode(false);
bnve.enableItemShiftingMode(false);
```

#### 自定义图标和文本大小 ####
```java
bnve.setIconSize(widthDp, heightDp);
bnve.setTextSize(sp);
```

#### 和 ViewPager 绑定####
```java
// set adapter
adapter = new VpAdapter(getSupportFragmentManager(), fragments);
bind.vp.setAdapter(adapter);

// binding with ViewPager
bind.bnve.setupWithViewPager(bind.vp);
```


#### 添加带数字的小红点 ####

1. Gradle 中加入 badge 库的依赖
	```
	compile 'q.rorbin:badgeview:1.1.0'
	```
2. 和底部控件绑定
	```
    // add badge
    addBadgeAt(2, 1);

    private Badge addBadgeAt(int position, int number) {
        // add badge
        return new QBadgeView(this)
                .setBadgeNumber(number)
                .setGravityOffset(12, 2, true)
                .bindTarget(bind.bnve.getBottomNavigationItemView(position))
                .setOnDragStateChangedListener(new Badge.OnDragStateChangedListener() {
                    @Override
                    public void onDragStateChanged(int dragState, Badge badge, View targetView) {
                        if (Badge.OnDragStateChangedListener.STATE_SUCCEED == dragState)
                            Toast.makeText(BadgeViewActivity.this, R.string.tips_badge_removed, Toast.LENGTH_SHORT).show();
                    }
                });
    }
	```

## 混淆 ##

如果你启用了 ProGuard，那你应该加上以下混淆代码:
```
-keep public class android.support.design.widget.BottomNavigationView { *; }
-keep public class android.support.design.internal.BottomNavigationMenuView { *; }
-keep public class android.support.design.internal.BottomNavigationPresenter { *; }
-keep public class android.support.design.internal.BottomNavigationItemView { *; }
```

## 致谢 ##

感谢 [Adrián Mouly](https://github.com/amouly) | [liaolintao](https://github.com/liaolintao) | [Luong Vo](https://github.com/luongvo).
感谢 [ittianyu](https://github.com/ittianyu)

