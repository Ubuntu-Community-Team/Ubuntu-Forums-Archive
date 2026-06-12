---
title: "Issues on 15&quot; 2010 Macbook Pro 6,2"
date: 2015-10-27
forum: Desktop Environments
---

### Post by jmartin235 on 2015-10-27
Hello! I just installed Xubuntu 15.10 on my old 15" Macbook Pro and have some annoying issues that I hope can be cleared up:

- I've installed mtouch for the trackpad & found various sites with "tweaked" settings but still have 2 problems with it. It works fine most of the time, but after using the keyboard, it doesn't respond for about a second. Also, if you tap on the far right side of the trackpad (either with my finger, usually accidentally with the bottom of my thumb while I'm typing), a right-click happens. Unless I'm missing something, that shouldn't occur with my settings:
zsh 135 % cat /usr/share/X11/xorg.conf.d/50-mtrack.conf 


Section "InputClass"
MatchIsTouchpad "true"
	Identifier "Multitouch Touchpad"
	Driver "mtrack"
	Option "Sensitivity" "0.2"
	Option "FingerHigh" "12"
	Option "FingerLow" "4"
	Option "IgnoreThumb" "true"
	Option "IgnorePalm" "true"
	Option "TapButton1" "0"
	Option "TapButton2" "0"
	Option "TapButton3" "0"
	Option "TapButton4" "0"
	Option "ClickFinger1" "1"
	Option "ClickFinger2" "3"
	Option "ClickFinger3" "3"
	Option "ButtonMoveEmulate" "true"
	Option "ButtonIntegrated" "true"
	Option "ClickTime" "25"
	Option "BottomEdge" "40"
	Option "ButtonEnable" "false"
	Option "ButtonZonesEnable" "false"
	Option "SwipeLeftButton" "8"
	Option "SwipeRightButton" "9"
	Option "SwipeUpButton" "0"
	Option "SwipeDownButton" "0"
	Option "ScrollDistance" "75"
	Option "ScrollUpButton" "4"
	Option "ScrollDownButton" "5"
	Option "ThumbSize" "35"
	Option "PalmSize" "55"
	Option "DisableOnThumb" "false"
	Option "DisableOnPalm" "true"
	Option "SwipeDistance" "1000"
	Option "ScrollLeftButton" "7"
	Option "ScrollRightButton" "6"
	Option "AccelerationProfile" "2"
	Option "ConstantDeceleration" "2.0" # Decelerate endspeed
	Option "AdaptiveDeceleration" "2.0" # Decelerate slow movements
EndSection

- Is there a good way to make the brightness buttons work on the screen? I can do it manually by changing the value in /sys/class/backlight/gmux_backlight/brightness, but is there a package/script that I can tie the buttons to?

Thanks!

---

