---
title: "Automount and auto-open question."
date: 2005-12-05
forum: Desktop Environments
---

### Post by z-vet on 2005-12-05
Hi all.
Well, i don´t like the way KDE 3.5 deals with removable media. First, a windoze-like popup asking me what do i want to do: i don´t need it at all and want to completely disable it: how? Second: it mounts a CD and USB card and it´s fine, but then it opens it in new Konqueror window... I want to disable this behavior too, just because i don´t use Konqueror. 
Thanks for any help.

---

### Post by michux on 2005-12-05
[QUOTE=z-vet]Hi all.
Well, i don´t like the way KDE 3.5 deals with removable media. First, a windoze-like popup asking me what do i want to do: i don´t need it at all and want to completely disable it: how? Second: it mounts a CD and USB card and it´s fine, but then it opens it in new Konqueror window... I want to disable this behavior too, just because i don´t use Konqueror. 
Thanks for any help.[/QUOTE]

Open Kcontrol. Then Peripheral devices -> Data storage devices and disable all.

BTW: I want exactly what you don't need, I want to see the popup, but it doesn't show. KDE 3.5 as well, with Kubuntu Breezy. Any hints?

---

### Post by Takis on 2005-12-05
Have a look in Settings->Peripherals->Storage Media, it should have all the settings you need.

---

### Post by aysiu on 2005-12-05
Try [this](http://www.ubuntuforums.org/showthread.php?t=90457&highlight=ivman)

---

### Post by z-vet on 2005-12-05
Thanks aysiu.

---

### Post by knowerrors on 2005-12-05
Im using kubuntu 5.10, with kde 3.5 installed from [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/)

When I plug in a usb flash drive, a notification window pops up asking to either "open in new window" or "do nothing". Clicking on "open in new window" opens konqueror in "system:/media" with an icon for the usb drive.  Clicking on that icon trys to mount it, but then says:
"
Could not mount device.
The reported error was:
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1
mount failed
"
so then I must  manually brouse to /media/sda1 to access my files...

Any way to fix this so that clicking on that icon will open /media/sda1?

Other issue: usb drive and cdrom do not show as mounted icon on the desktop, even though this option is enabled.  How to fix?

I also tried uinnstalling ivman... still have the same problem.  Any other ideas?  

Knowerrors

---

