---
title: "Keyboard shortcut - multimedia key"
date: 2008-05-06
forum: Desktop Environments
---

### Post by T_Beermonster on 2008-05-06
I'm unsure if this is quite the right subject area but it looks like a best fit to me.

I am using a logitech internet pro keyboard with several extra function keys with ubuntu 8.04 (Hardy). That keyboard isn't listed in system-preferences-keyboard-layouts-keyboard model but the "logitech internet keyboard" seems to be fine. The only problem is that the Launch media player key does not work, all other shortcut keys seem to work (play/pause, mute, volume up/down, favorites, email, browser) just that one key doesn't.
It doesn't seem to be a hardware issue since I can go to system-preferences-Keyboard Shortcuts and define that key as the launch media player key by pressing it(detects as XF86AudioMedia). But once defined it still has no effect, nor does it have any effect if I map that key to do something else (open home folder for example).
I can set a different keyboard shortcut, but only some of these will have an effect once defined (Alt-m will work as will delete, AltGr-m will not).

It isn't a great hardship having one key that I cant get any use from, but it is kind of annoying knowing that the key press is detected, the key is mapped to a task, but the task wont be done when the key is pressed.

There are a few other comments about media keys not working, but none seem to match the case where the media player of choice can be launched by shortcut, the key is detected, the shortcut is defined but nothing happens.

Does anyone else have this problem? Has anyone else found a fix for it?

---

### Post by warp99 on 2008-05-06
> **T_Beermonster said:**
> I'm unsure if this is quite the right subject area but it looks like a best fit to me.

I am using a logitech internet pro keyboard with several extra function keys with ubuntu 8.04 (Hardy). That keyboard isn't listed in system-preferences-keyboard-layouts-keyboard model but the "logitech internet keyboard" seems to be fine. The only problem is that the Launch media player key does not work, all other shortcut keys seem to work (play/pause, mute, volume up/down, favorites, email, browser) just that one key doesn't.
It doesn't seem to be a hardware issue since I can go to system-preferences-Keyboard Shortcuts and define that key as the launch media player key by pressing it(detects as XF86AudioMedia). But once defined it still has no effect, nor does it have any effect if I map that key to do something else (open home folder for example).
I can set a different keyboard shortcut, but only some of these will have an effect once defined (Alt-m will work as will delete, AltGr-m will not).

It isn't a great hardship having one key that I cant get any use from, but it is kind of annoying knowing that the key press is detected, the key is mapped to a task, but the task wont be done when the key is pressed.

There are a few other comments about media keys not working, but none seem to match the case where the media player of choice can be launched by shortcut, the key is detected, the shortcut is defined but nothing happens.

Does anyone else have this problem? Has anyone else found a fix for it?

I use Keytouch with my Logictech 300 Multimedia Keyboard and it works great. If your key layout is not specified you can download the correct one from the developers site or build your own with the Keytouch editor. Make sure you enable the universe repositories, then:
```
 sudo apt-get install keytouch
```
if you need the editor append "keytouch-editor' to the end of the previous command string.

---

