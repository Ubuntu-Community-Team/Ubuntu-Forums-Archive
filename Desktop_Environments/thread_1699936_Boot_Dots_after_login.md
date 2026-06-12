---
title: "Boot Dots after login"
date: 2011-03-04
forum: Desktop Environments
---

### Post by FrankX.190875 on 2011-03-04
I have to say, this is most possibly the most annoying thing I've had on Ubuntu...

When ubuntu boots it shows the lil white and orange dots across the middle of the screen while its loading.

On my pc, these dots do not go away or STOP during or AFTER login!?! They are even showing ALWAYS ON TOP most of the time!

As lovely as they are, I'm sure they shouldn't be there after or even during log on.

[IMG]http://i3.photobucket.com/albums/y92/FrankX/ForumPics/ubuntu_dots.png[/IMG]

Any ideas whats going on and how to get shut of them???

Ta'

FrankX

---

### Post by Krytarik on 2011-03-04
Wow, that's indeed really weird! I didn't see that so far.

Without googling about it (I wonder if it would help in that case), I have some options at hand:

- Try these workarounds, from the plymouth readme (/usr/share/doc/plymouth/README.Debian):
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

For nVidia and ATI users, the default "nouveau" and "radeon"
drivers are Kernel Mode Setting enabled, but do not always
provide 3D capability at the current time. By switching to
using the restricted/non-free nvidia-glx or fglrx drivers,
you will gain 3D capability at the loss of a high-color
splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
/etc/default/grub
sudo update-grub

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u- Switch to another Plymouth theme, see my earlier post, the lower part:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

- Turn off Plymouth at all: Remove "quiet splash" or just "splash" from the "GRUB_CMDLINE_LINUX_DEFAULT" options in "/etc/default/grub" and run "sudo update-grub" after that.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by FrankX.190875 on 2011-03-05
Krytarik thanks for the reply.

I managed to get rid of them (more by accident than plan)...

I had changed the login screen to XDM instead of GDM.
When I worked out how to change this back the dots went away.

Weird! A case of if it ain't broke don't fix it. :P

---

