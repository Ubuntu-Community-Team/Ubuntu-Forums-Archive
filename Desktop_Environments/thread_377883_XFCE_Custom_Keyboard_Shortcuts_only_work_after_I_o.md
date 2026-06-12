---
title: "XFCE Custom Keyboard Shortcuts only work after I open Keyboard Settings"
date: 2007-03-06
forum: Desktop Environments
---

### Post by rocktorrentz on 2007-03-06
I have recently got a new keyboard which has media keys and so I found a guide to make a custom keyboard layout and make them work which involved making a custom xmodmap.conf and adding "xmodmap xmodmap.conf" to Autostarted Applications and then using Keyboard Settings to add extra shortcuts. However in order to make the extra keyboard shortcuts work again after a reboot I have to open Keyboard Settings. Is there any way to make this automated?

Thanks
rocktorrentz

---

### Post by smaxer on 2007-05-30
I have exact the same problem here!! its ridiculous!

Can you please tell me how you solved this problem?? 

regards samxer

---

### Post by rocktorrentz on 2007-05-30
> **smaxer said:**
> I have exact the same problem here!! its ridiculous!

Can you please tell me how you solved this problem?? 

regards samxer
Sorry I didn't manage fix the problem and have since switched to Ubuntu Feisty.

---

### Post by RedSquirrel on 2007-06-01
> **rocktorrentz said:**
> I have recently got a new keyboard which has media keys and so I found a guide to make a custom keyboard layout and make them work which involved making a custom xmodmap.conf and adding "xmodmap xmodmap.conf" to Autostarted Applications and then using Keyboard Settings to add extra shortcuts. However in order to make the extra keyboard shortcuts work again after a reboot I have to open Keyboard Settings. Is there any way to make this automated?

Thanks
rocktorrentz
I don't have Xubuntu, so I can't test this, but you might try putting your xmodmap settings in the file ~/.Xmodmap rather than using the "Autostarted Applications". It may not make any difference, but it might be worth a shot. ;)

EDIT: all you have to do is put the settings in ~/.Xmodmap. gdm will load them automatically, so don't put the xmodmap in front of your settings. In your case, whatever you had in "xmodmap.conf" should be in ~/.Xmodmap.

---

### Post by smaxer on 2007-06-04
> **RedSquirrel said:**
> 
EDIT: all you have to do is put the settings in ~/.Xmodmap. gdm will load them automatically, so don't put the xmodmap in front of your settings. In your case, whatever you had in "xmodmap.conf" should be in ~/.Xmodmap.

That was the f*** solution! i stored my settings in ~/.Xmodmap.cp and loaded them with the autostart. Now they are stored in ~/.Xmodmap and it works.


THANKS!!

regards, smaxer

---

### Post by fifafrazer on 2007-10-28
I have the same problem, and it is not caused by missing symlinks. XEV returns the right symlinks, f.ex.
```
KeyRelease event, serial 31, synthetic NO, window 0x2e00001,
    root 0x1a5, subw 0x0, time 3895664250, (65,442), root:(499,668),
    state 0x0, keycode 153 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
I have to open the keyboard settings program before my shortcuts work.

EDIT: A very odd thing is, that my raise/lower volume and mute media keys work before i open keyboard settings, but the XF86Next, XF86Prev, XF86Mail etc. keys don't, though the right symlink is shown by xev. And it is not caused by the system not loading my custom shortcut file, because my non-media-key custom shortcuts like Super+v works before opening the keyboard setting program. The issue is only related to my custom media keys shortcuts. I'm stuck troubleshooting this problem.

---

### Post by fifafrazer on 2007-11-03
bump: I know my problem sounds weird, but isn't there anyone with some kind of suggestion? What is it that is launched by the keyboard config program in order to make my special keys work?

---

### Post by RedSquirrel on 2007-11-05
Which version of Xfce are you using? Is this on gutsy? 

It just sounds like a bug to me. For instance:

[http://bugzilla.xfce.org/show_bug.cgi?id=2731](http://bugzilla.xfce.org/show_bug.cgi?id=2731)

If you want to dig deeper, I would recommend searching in Google to see what you come up with and maybe looking around on that bugzilla site a bit more. Good luck.

---

### Post by fifafrazer on 2007-11-09
Yes, I'm using gutsy..

It seems to be a bug..

The about page gives me:
Xfce 4 Desktop Environment
version 4.4.1 (Xfce 4.4)

---

### Post by mabhobs on 2008-07-16
Workaround: Use XBindKeys as described in [http://www.linux.com/articles/59494]("http://www.linux.com/articles/59494").

---

