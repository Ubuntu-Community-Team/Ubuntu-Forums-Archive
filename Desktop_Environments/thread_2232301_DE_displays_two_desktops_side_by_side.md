---
title: "DE displays two desktops side by side"
date: 2014-07-01
forum: Desktop Environments
---

### Post by eclark461 on 2014-07-01
After recently updating my sofware through software update i noticed that my desktop display showed two mirrorred displays instead of one.

I have tried everything and searched extensively about resolving it to no avail.

[ATTACH=CONFIG]254368[/ATTACH]

---

### Post by QIII on 2014-07-01
Hello!

Please be considerate of those who have slow connections or data restrictions.  Instead of pasting a large image, please use the attachment functionality (the paperclip symbol above the text entry box) to attach the image.

Thanks!

Cheers!

---

### Post by kansasnoob on 2014-07-01
That appears to be a "flashback/classic" session but it would be helpful to know what version of Ubuntu you're running.

One thing I wonder is if you're running a Compiz session you might just try a Metacity session to see what happens.

---

### Post by eclark461 on 2014-07-03
I have tried with every single desktop from Classic to Ubuntu to Ubuntu 2D

Even at the login screen it does the same thing

It is almost like it is detecting two monitors, however there is only one on the system and it when I hit detect Displays it only displays one.

12.04 LTS fully updated.

---

### Post by kansasnoob on 2014-07-04
Since it also effects the login screen I suspect either a graphics or kernel issue but first rule out a settings issue by trying a guest session.

If it still does that in a guest session I'd try booting an older kernel from the grub menu.

---

### Post by Empty_Next on 2014-07-05
[ATTACH=CONFIG]254480[/ATTACH][ATTACH=CONFIG]254479[/ATTACH][HR][/HR][HR][/HR][HR][/HR][HR][/HR][HR][/HR][COLOR="#800000"][/COLOR][SIZE=3][/SIZE][FONT=Century Gothic][/FONT][FONT=Book Antiqua][/FONT]Same here. I use VM Ware player version 6 and used an the 12.04 LTS first. after running the updates I got the double screens as well.  I installed the 14.04 LTS and after the updates, same issue. cannot untick the mirror option in system settings as it does only detect one monitor. the laptop screen. it does have 2 graphics adapters, an intel HD 4600 and an AMD R5 230. the intel chipset is used as primary graphics GPU.  anyway I attached a screenshots from login and from the desktop,. the option to shutdown, the menu is not painted in the UI so one has to guess where to click in the menu header and then estimate some inches down for the valid menu item.. ( shutdown or reboot or suspend etc..)

I do think it is related to  a combination of the latest update and Unity. There is quite some info on the inet on how to disable certain settings and indeed try various kernels or KDE, Gnome, Ubuntu's 3D or 2D options. 

I will test once more with an older kernel as it is a trial and error VM in the first place. get back in this asap

E.N

---

### Post by Empty_Next on 2014-07-05
[ATTACH=CONFIG]254481[/ATTACH]
booting via grub : 3.13.0.24-generic version

then the issue does not  occur. when booting again using the 3.13.0.31-generic. the issue is back.  at least there is a work around.

E.N

---

### Post by kansasnoob on 2014-07-05
I've never had the hardware to test on so I don't know much about the Optimus thing but have a read:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

And I know from following Ubuntu GNOME dev that it doesn't work properly with gdm:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1262068](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1262068)

---

### Post by Empty_Next on 2014-07-07
it is related to the update on 12.04 and on 14.04.. when i  boot to grub and select the old kernel image all is fine.. . it is guit easy to test by installing a latest ubuntu version either on vmware or on a small usb drive or so.. or just buy the Laptop and file it under: research costs..

---

### Post by Empty_Next on 2014-07-09
it is acknowledeged as a kernel issue.  : [https://communities.vmware.com/thread/481038](https://communities.vmware.com/thread/481038)

so   there is no solution yet, but as stated, use the work around  as mentioned before. 

cheers

---

