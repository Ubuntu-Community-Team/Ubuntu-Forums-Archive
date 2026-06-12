---
title: "Power Button not working - Lubuntu"
date: 2012-08-25
forum: Desktop Environments
---

### Post by decomp on 2012-08-25
Hello I am running Lubuntu 12.04 and on two seperate machines the power button does not work after a clean install.

I have made sure that /.config/openbox/lubuntu-rc.xml contains the correct keybinding:

```
    <keybind key="XF86PowerOff">
      <action name="Execute">
        <command>lubuntu-logout</command>
      </action>
    </keybind>
```

I have also tried installing acpid.

xev responds when I press the power button so the button itself is fine. The button also works fine in gnome 3 or xfce.

How can I get the power button working again?

---

### Post by Rodney9 on 2012-08-25
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by decomp on 2012-08-25
Thanks for the links! As I stated in my first post, I have already configured openbox correctly. I did use the xev command recommended on your first link and here's what I found:

```
hiro@hiro-laptop:~$ xev | grep "keycode"
   request MappingKeyboard, first_keycode 8, count 248
```

there's no mention of XF86poweroff. All other special keys give their keycode output! for example my volume up button:

```

hiro@hiro-laptop:~$ xev | grep "keycode"
   state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume),
   same_screen YES,
```

So it's not bound to xf86poweroff somehow? In fact the whole format looks wrong. Why does it work in gnome though?

---

### Post by decomp on 2012-08-27
.

---

### Post by decomp on 2012-08-28
.

---

### Post by decomp on 2012-08-30
.

---

### Post by decomp on 2012-09-05
Well I wrote to the lubuntu mailing list and got no reply. Sigh.

---

### Post by philisper on 2012-09-11
Hello,

have you found a solution so far?
I have exactly the same problem.

Thanks

---

### Post by thatguymark on 2012-11-09
I found that if you just use the Power Manager under the Preferences menu you can set the button to shut down, (eee PC 1000HD fwiw) but not "ask" which is basically lubuntu-logout - when set to Ask it does nothing. Suspend also works.

---

