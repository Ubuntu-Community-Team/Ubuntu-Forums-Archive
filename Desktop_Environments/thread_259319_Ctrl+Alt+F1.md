---
title: "Ctrl+Alt+F1"
date: 2006-09-17
forum: Desktop Environments
---

### Post by ART_Adventures on 2006-09-17
Hello People,

In order to solve an issue somebody has asked me to bring up a command prompt by pressing Ctrl+Alt+F1. However, if I press this combination at the login screen, nothing happens.

Someone mentioned about changing the menu.lst for grub. I changed this so that the relevant section reads:

```

# defoptions=quiet

```

This was changed from # defoptions=quiet splash

However, this does not appear to have made a difference. I still cannot bring up any command prompt using Ctrl+Alt+F1. Can anybody help me?

Thanks.

---

### Post by Timothy Butwinick on 2006-09-17
What do you mean by "login screen"? Judging by the talk about GRUB, I suppose you mean GRUB's startup screen, and I'm not sure if you can use Ctrl-Alt-F1 there.

---

### Post by DoktorSeven on 2006-09-17
Well, he said "command prompt" so I assume he means a text terminal.  Holding CTRL + ALT then pressing F1 should indeed bring up the text window, as should any function key below F7 (F1-F6) when pressed while holding CTRL+ALT.  Try some of the other keys, and make sure you're holding CTRL+ALT *before* pressing one of the F-keys.  That's all I can think of...

---

### Post by Ramaddan on 2007-10-25
Hi,

I have the same problem here.

After upgrading to Gutsy from Feisty, I could no longer bring up the terminal with Ctrl+Alt+F1

Did anyone else get  this issue?

Thanks

---

### Post by Shimmy on 2007-10-25
> **Ramaddan said:**
> Hi,

I have the same problem here.

After upgrading to Gutsy from Feisty, I could no longer bring up the terminal with Ctrl+Alt+F1

Did anyone else get  this issue?

Thanks

Mine ctrl+alt+F1 works, however i noticed that my xserver has moved from ctrl+alt+f7 to ctrl+alt+f9.

By the way, why don't just use gnome-terminal? :)

---

### Post by ktulu1115 on 2007-10-25
Same problem here.  Only thing I found to work was to disable compiz (it's causing me a lot of grief).  Sometimes you need the virtual terminals for an emergency purpose (like X not working)

---

### Post by aletheianalex on 2007-10-25
ctrl+alt+<function key> does not bring up a text screen... actually, none of the TTY's work!!!  And when I try to bring up the terminal, the desktop/window manager crashes, the screen goes black and I end up back at the login screen!!!

This is a REAL bad problem, and I am considering downgrading because of it!!

Someone please help... SOON!

---

### Post by frbe0101 on 2007-10-25
Just so a newbie like me knows, how do i get back to the gui from a command prompt after pushing Ctrl+Alt+F1 out of stupid curiosity?

---

### Post by aletheianalex on 2007-10-25
> **frbe0101 said:**
> Just so a newbie like me knows, how do i get back to the gui from a command prompt after pushing Ctrl+Alt+F1 out of stupid curiosity?

It should be Ctrl+Alt+F7 or possibly Ctrl+Alt+F9 in some cases.

---

### Post by frbe0101 on 2007-10-26
> **aletheianalex said:**
> It should be Ctrl+Alt+F7 or possibly Ctrl+Alt+F9 in some cases.

Ctrl+Alt+F7 works thanks.

---

### Post by aletheianalex on 2007-10-26
> **Ramaddan said:**
> Hi,

I have the same problem here.

After upgrading to Gutsy from Feisty, I could no longer bring up the terminal with Ctrl+Alt+F1

Did anyone else get  this issue?

Thanks

After some searching... i see that it is an official BUG... and a horrible one at that.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910")

I got it fixed on my machine... but it took all night.

This finally did it:

Ran 'sudo nano /boot/grub/menu.lst' Deleted my "vga=xxx"  argument

Ran: 'sudo update-grub'

Used 'sudo nano /etc/usplash.conf' to correct resolution for splash 

Used 'sudo nano /etc/initramfs-tools/modules' to add fbcon and vesafb 

Used 'sudo nano /etc/modprobe.d/blacklist-framebuffer'  to comment out fbcon and vesafb

<<Desperately enabled every possible repository in hopes of a fix in the works and ran 'sudo aptitude update' and then  'sudo aptitude safe-upgrade' (you can skip these steps probably)>>

Ran: 'sudo depmod -a'

Ran: 'sudo dpkg-reconfigure usplash'

That did it , but there are still a few other problems.

---

### Post by Ramaddan on 2007-11-01
Thanks aletheianalex :)

I have my Ctrl+Alt+F1 back now.

Thank you very much. :)

---

### Post by kishorebudha on 2007-12-24
I applied it to my fresh install of Gutsy on Inspiron 6000 (1.73ghz, ATI Mobility Radeon x300) and your recommendations worked! Thanks.

---

### Post by kishorebudha on 2007-12-24
The shutdown splash is displayed in weird psychedelic colours, which was resolved by re-downloading and re-installing the usplash

```
aptitude search usplash
```

from the resulting options i installed the default ubuntu splash theme

```
sudo aptitude install usplash-theme-ubuntu
```

lastly updated the "initial RAM disk",

```
sudo update-initramfs -u
```

---

