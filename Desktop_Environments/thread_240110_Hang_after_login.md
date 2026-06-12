---
title: "Hang after login"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Maxtr0sity on 2006-08-20
So I was playing around with ATI drivers and now I can't get to the desktop.  Ubuntu starts fine, I can login, but then the background loads but nothing else.  I've let it sit for a few hours without any change.  I can move the mouse and keyboard is responsive.  When I press power off, it goes through everything normal.

I tried booting into safe mode but same problem occurs.

---

### Post by b_martinez on 2006-08-20
I'm not really sure, but I think you will have to re-configure your /etc/X11/xorg.conf file. Either that or re-install the correct ATI driver. You may have one that is 'close, but no cigar'. 
Then again, I may be wrong, 'cuz Iuse an Nvidia card.
Bill

---

### Post by Maxtr0sity on 2006-08-20
How can I go about editing the file without booting to desktop?

Also, how can I edit menu.lst (usually sudo gedit /boot/grub/menu.lst) outside of the GUI?

---

### Post by b_martinez on 2006-08-20
> **Maxtr0sity said:**
> How can I go about editing the file without booting to desktop?

Also, how can I edit menu.lst (usually sudo gedit /boot/grub/menu.lst) outside of the GUI?

1)boot into recovery mode
2)log on
3)vim /etc/X11/xorg.conf  <--- vim is an editor 
4)these will allow you to edit
navigate with the up/down arrows
'insert' key will allow you to add text
"delete' key will do just that
'esc' key will take you out of 'insert' or 'delete' mode , which CANNOT be used together
once out of 'insert'/'delete' mode, when all is as it should be, 
:wq 
will write out/quit editor
Bill

p.s. ever use the editor named 'nano'?
p.p.s. works with /boot/grub/menu.lst also

---

### Post by taurus on 2006-08-20
If you are a newbie, use nano as your text editor instead of vi/vim because it will beep the heck out of you if you hit a wrong key!!!  Learn how to use vi/vim later when you have time...

---

### Post by Maxtr0sity on 2006-08-20
I'm a quick learner.  I just fixed my grub problem with VIM (learned to think before I type to avoid beeps).  Changed back my old xorg.conf file but still no avail, any other suggestions?

---

### Post by taurus on 2006-08-20
Which driver did you use in /etc/X11/xorg.conf?  Try resetting it back to vesa...

```

Driver            "vesa"

```

---

