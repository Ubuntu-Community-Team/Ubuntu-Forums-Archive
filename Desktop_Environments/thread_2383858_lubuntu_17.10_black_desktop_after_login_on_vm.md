---
title: "lubuntu 17.10 black desktop after login on vm"
date: 2018-01-30
forum: Desktop Environments
---

### Post by syengulalp on 2018-01-30
Running in VirtualBox 5.2.6,  I tried to maximize the screen for full screen at 1920x1080 using the built in GUI tool, after restart I get the log in screen, once I enter username and password, screen goes to full black. 

Any ideas how to get it to work?

Thanks,
S.

---

### Post by cruzer001 on 2018-01-30
Your on Wayland.

At the boot screen (grub), advance options, switch back to xorg and see what happens.

[https://ubuntuforums.org/showthread.php?t=2379557](https://ubuntuforums.org/showthread.php?t=2379557)

---

### Post by syengulalp on 2018-01-30
> **cruzer001 said:**
> Your on Wayland.

At the boot screen (grub), advance options, switch back to xorg and see what happens.

[https://ubuntuforums.org/showthread.php?t=2379557](https://ubuntuforums.org/showthread.php?t=2379557)

Not sure how to do this, in grub menu -> advanced -> Ubuntu, with .....

when I hit e, and see the grub command parameters, I do not see anything to switch to xorg.

Could you elaborate some more?

Thanks again,
S.

---

### Post by syengulalp on 2018-01-30
I did try the recovery mode, and at least now I have the desktop after login. How do I pick between wayland and xorg as a permanent option?

S.

---

### Post by #&amp;thj^% on 2018-01-30
Here is a good link for that: [https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10](https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10)

if you want to use Xorg on every login you can edit: "/etc/gdm3/custom.conf and uncomment the line"
 

```
#WaylandEnable=false 
```
by removing the # in front.

Save the file and then on reboot you will never see the cog asking for which session to use.

---

### Post by syengulalp on 2018-01-30
I don't see a gdm3 folder in my /etc/, do you think that is available maybe only in ubuntu but not lubuntu?

S. 

> **1fallen said:**
> Here is a good link for that: [https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10](https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10)

if you want to use Xorg on every login you can edit: "/etc/gdm3/custom.conf and uncomment the line"
 

```
#WaylandEnable=false 
```
by removing the # in front.

Save the file and then on reboot you will never see the cog asking for which session to use.

---

### Post by #&amp;thj^% on 2018-01-30
My fault, I did not see "Lubuntu" they use Openbox and there should not be a wayland option to login to.

---

### Post by cruzer001 on 2018-01-30
Also my mistake, sorry.  I do not know how I missed that!  Lubuntu does not use wayland at all.

---

### Post by cruzer001 on 2018-01-30
> **syengulalp said:**
> I did try the recovery mode, and at least now I have the desktop after login.

Can you now boot normally?  If not, try setting nomodeset for one boot.

[https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by panix2 on 2018-04-17
> **syengulalp said:**
> Running in VirtualBox 5.2.6,  I tried to maximize the screen for full screen at 1920x1080 using the built in GUI tool, after restart I get the log in screen, once I enter username and password, screen goes to full black. 

Any ideas how to get it to work?

Thanks,
S.

My case looks like yours.
I'll find tips - 
**delete or rename .config into your user homedir**
and it's work for me

---

### Post by jorlando on 2019-01-04
Delete this file:

~/.config/autostart/lxrandr-autostart.desktop

reboot.

Now retry other resolutions, only press SAVE if the new resolution tests ok (the 15 seconds warning, etc)

If by accident you lose your desktop just remove lxrandr-autostart.desktop and reboot again.

---

### Post by QIII on 2019-01-04
Ubuntu 17.10 is no longer supported and this thread is nearly a year old.

Rest in peace.

Closed.

---

