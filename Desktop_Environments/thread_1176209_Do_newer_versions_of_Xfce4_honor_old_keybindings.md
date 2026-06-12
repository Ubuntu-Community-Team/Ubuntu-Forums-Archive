---
title: "Do newer versions of Xfce4 honor old keybindings?"
date: 2009-06-02
forum: Desktop Environments
---

### Post by slaufer on 2009-06-02
I just installed Xubuntu 9.04 on my new laptop, and I quickly noticed that the window manager settings window no longer has bindings for independent window moving/resizing, or a keybinding to open the menu. I've been using the same keybinding settings for many years in several different window managers, so this is an issue for me, especially on a laptop, since I avoid using the touchpad at all costs.

I was hoping someone could tell me if the current version of Xfwm4 would honor my old keythemerc if I were to dig it up from somewhere, or if it'd just ignore the old settings. Thanks.

---

### Post by kerry_s on 2009-06-02
i'm not sure what you mean, it's very easy to set, you just double click on it, press the keys you want, done.
even creating shortcuts is easier, click add, put your command and press the keys.

---

### Post by slaufer on 2009-06-02
Older versions of xfce had hotkeys to move/resize windows in different directions independently. There were seperate bindings for up, down, left and right, as well as some other bindings that seem to be gone now.

Apparently the config format has completely changed as well. The ~/.themes/<themename>/xfwm4/keythemerc has been replaced with ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml, which is not at all the same.

Nonetheless, I dug up my old config file and tried to convert it. However, it seems that the {move,resize}_window_{up,down,left,right}_key and popup_menu keys are no longer supported in the new format.

Unfortunately, this is kind of a dealbreaker for me, since the highly customizable hotkeys were what attracted me to Xfce4 in the first place, because I spend a lot of time in cramped spaces/moving with my laptop, which makes using the touchpad nigh unto impossible.

Anyway, any advice would be appreciated, especially if there's something I'm missing here.

---

### Post by kerry_s on 2009-06-02
> Older versions of xfce had hotkeys to move/resize windows in different directions independently. There were seperate bindings for up, down, left and right, as well as some other bindings that seem to be gone now.

move window= alt+f7 and use the arrow keys, esc(escape) to finish
resize=alt+f8 and use the arrow keys, esc(escape) to finish
(both changeable of course)
are you looking in the right place? settings manager> window manager> keyboard tab


> Unfortunately, this is kind of a dealbreaker for me, since the highly customizable hotkeys were what attracted me to Xfce4 in the first place, because I spend a lot of time in cramped spaces/moving with my laptop, which makes using the touchpad nigh unto impossible.

Anyway, any advice would be appreciated, especially if there's something I'm missing here. 

there are window managers that are made more for keyboard control.
it's your call, i'm not 1 to judge, to me the shortcuts are there or easy to setup.

---

