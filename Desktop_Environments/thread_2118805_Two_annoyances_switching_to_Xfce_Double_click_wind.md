---
title: "Two annoyances switching to Xfce: Double click window title bar / hot key Workspace"
date: 2013-02-22
forum: Desktop Environments
---

### Post by mdlueck on 2013-02-22
Greetings,

Two sharp spots since upgrading to 12.04 and deciding to go with Xubuntu.

1) Double clicking a window title bar does not maximize / un-maximize the window.

2) The Workplace Switcher component responds to Ctrl-F# key combinations jumping to that number virtual desktop. I use these in my applications, and can not since Workplace Switcher has taken them hostage.

Ubuntu 10.04 did not have these annoying behaviors. Is there some way to adjust those sharp spots? TIA!

---

### Post by LewisTM on 2013-02-22
The double-click action used to be in Settings -> Window Manager -> Advanced but is no longer present for some reason.
You can still change the behavior manually. Run
```
xfce4-settings-editor
```
Go to xfwm4 channel and change the **double_click_action** property to **maximize**.

You can edit the window manager keyboard shortcuts by going in Settings -> Window Manager -> Keyboard. Double-click the shortcut and press the Clear button. I have removed many since by default the Window Manager preallocates shortcuts for 12 workspaces (!).

Cheers!

---

### Post by mdlueck on 2013-02-23
Greetings LewisTM,

The first suggestion appears to already be configured thusly:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231804&stc=1&d=1361640242[/IMG]

I had to recreate it as I accidentally deleted it. However, I think I managed to put it back correctly, then captured this screen shot. Please confirm accuracy.

Double click momentarily switches the mouse to an hourglass icon, then back to the pointer.

Your second suggestion worked perfectly!!! Presently I am running with 14 virtual desktops, so it was getting very annoying switching VD's as I am a moderate F-key user.

---

### Post by r.stiltskin on 2013-03-03
In addition to the Settings Editor, the double-click action "supposedly" can be set by opening the Settings dialog called "Window Manager".  Under the Advanced tab, if you scroll down to the last item which is Double-click action you can select shade, hide, maximize, fill or nothing.  Whether you do it in the Settings Editor or in Window Manager Settings, it sets the value you choose in ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml.

Unfortunately it doesn't seem to matter which action you choose.  As far as I can see, that config file is ignored and double-clicking on a title bar does nothing.  It's not working for me in either Xubuntu 12.04 32-bit or 12.10 64-bit.

---

### Post by darkcrimson on 2013-03-03
I just tried this and got the same as you. It seems the configuration is completely bypassed for some reason. This is odd...

---

### Post by Toz on 2013-03-03
Try changing the mouse double-click Time and Distance settings to see if that helps (Settings Manager -> Mouse and Touchpad -> Behaviour). Perhaps the settings are too low and the double-click event doesn't happen fast enough (or the mouse moves too much).

---

### Post by r.stiltskin on 2013-03-04
Thanks Toz.   That fixed it.  My double-click threshold was set at 250 ms.  I raised it to 400 ms and now double clicking on the title bar has the desired effect.

---

### Post by mdlueck on 2013-03-08
Thank you both, raising the time to 400ms corrected the behavior for me as well.

That one I think I will research how to suggest to Ubuntu to change the default as what it was set to was impossible to obtain.

Thanks again!

---

### Post by mdlueck on 2013-03-09
Turns out the adjustment to 400 was already in the bug tracker...

[xfce]Double click title bar actions use different speed than text selection
[https://bugs.launchpad.net/xfwm4/+bug/393672](https://bugs.launchpad.net/xfwm4/+bug/393672)

I subscribed and commented.

---

