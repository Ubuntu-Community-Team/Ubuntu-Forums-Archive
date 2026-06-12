---
title: "Display settings popups when changing brightness"
date: 2013-12-19
forum: Desktop Environments
---

### Post by andy.baer on 2013-12-19
Hi

I've Ubuntu Studio 13.10 on an Lenovo E535 with AMD Radeon HD 7520G integarted graphic card. I had to change to the proprietary fglrx drivers for 2 reasons, first of all my laptop was getting really hot and secondly the display of certain graphics (eg waveform in audacity) did not work properly. With the prorietary drivers, these things just went away. BUT
Now, when I change the screen brightness with the corresponding hardware keys, the display brightness changes correctly, the toast in the upper right corner displays the current brightness level correctly but for each key click I get 2 display settings popups (xfce4-display-settings). I tracked them with xprop and the output is below.

Any help would be greatly appreciated!
Andy

_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 60817446
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_DIALOG
_NET_WM_USER_TIME_WINDOW(WINDOW): window id # 0x3a00025
WM_CLIENT_LEADER(WINDOW): window id # 0x3a00001
_NET_WM_PID(CARDINAL) = 14383
WM_LOCALE_NAME(STRING) = "en_US.UTF-8"
WM_CLIENT_MACHINE(STRING) = "andy"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
        program specified minimum size: 426 by 286
        window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "xfce4-display-settings", "Xfce4-display-settings"
WM_ICON_NAME(STRING) = "Display"
_NET_WM_ICON_NAME(UTF8_STRING) = "Display"
WM_NAME(STRING) = "Display"
_NET_WM_NAME(UTF8_STRING) = "Display"

---

### Post by Toz on 2013-12-19
Hello and welcome to the forums.

Is xfce4-display-settings somehow mapped to that key combination/event? You can check your xfce4-display-settings keyboard mappings with:
```
cat ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml | grep xfce4-display-settings
```

Which (if any) keyboard events are sent when you press the brightness function keys:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...and click on one of the brightness key combinations. Check the terminal for any codes that appear.

---

### Post by andy.baer on 2013-12-20
hi toz

that was it! removed these lines and the issue is gone

<property name="XF86Display" type="string" value="xfce4-display-settings --minimal"/>
<property name="&lt;Super&gt;p" type="string" value="xfce4-display-settings --minimal"/>

i thought it would be an issue on a lower level since it only came up once i changed the video driver. 

thank you very much for your help!

---

### Post by Toz on 2013-12-20
> **andy.baer said:**
> hi toz

that was it! removed these lines and the issue is gone

<property name="XF86Display" type="string" value="xfce4-display-settings --minimal"/>
<property name="&lt;Super&gt;p" type="string" value="xfce4-display-settings --minimal"/>

i thought it would be an issue on a lower level since it only came up once i changed the video driver. 

thank you very much for your help!

I think it still might be something lower level thats wrong with the driver. It would appear that when you press the brightness key combinations, the XF86Display event is being triggered, which it shouldn't be. Just to confirm, can you run the xev command from my previous post and press the key combination to see which code is being sent.

---

### Post by andy.baer on 2013-12-20
Sure, below is the output of your command:

235 XF86Display
235 XF86Display

that's why i got 2 windows for every click...

---

