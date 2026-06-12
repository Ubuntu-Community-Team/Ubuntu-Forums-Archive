---
title: "Upgraded Video Card -- can't login"
date: 2008-12-22
forum: General Help
---

### Post by Chachee on 2008-12-22
Hey all,
  Running 8.10 current.

  Upgraded from an ATI 9600XT, to a ATI 2600HD XT.  Both were AGP.  I am not running restricted drivers.  I get the splash screen, then the monitor goes into power saver mode.  No response to keyboard entry.  No response to ctrl+alt+backspace, ctrl+n, ctrl+alt+del.

  I've tried both DVI interfaces on the card to see if it switches from my XP partition. 

  I can't do anything with my primary system now since I can't login.  I tried searching the forums but nothing relevant came up.

  Don't know what to do.  I don't want to reinstall again.

  Thanks.

JT

---

### Post by Shazaam on 2008-12-22
Two things you can try...
1. When your pc boots and you see the grub screen saying "Hit ESC to..." etc. hit your ESC key. Highlight the first Ubuntu kernel entry; hit your e key. This will open the kernel line for editing. Add this to the end...
```
vga=791
```
or...
```
vga=782
```
After you enter it press your b (for boot) key and see if it will boot up. This is a temporary fix only good for that bootup. You would have to add it permanently to menu.lst but this is only to see if it will boot.

2. Same as above but when you see the grub kernel entries choose "Recovery Mode". It "should" get you to a choice of things to do; choose xfix and see if it does anything.

---

### Post by Chachee on 2008-12-23
Thanks for the reply, I'll try that out.  I tried running a 8.10 live CD to see if that had any change as well.  No joy.

I am running this on a 24in monitor.  Will that effect things?

JT

---

