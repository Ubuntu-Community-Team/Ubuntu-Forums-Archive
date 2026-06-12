---
title: "Digikam problems"
date: 2005-05-02
forum: Desktop Environments
---

### Post by tristure on 2005-05-02
Hi,

I experience some annoying problems with digikam, did anyone have the same problems?

1) (not very serious, but still a little pain) When accessing a digital camera, connexion only succeeds the first time you plug it in.
If you unplug it, then plug it again in the same KDE session, the connexion won't work. I have to reboot in order to make it work again.
Well, I rarely have to plug my camera multiple times during the same session, but it should be fixed anyway.

2) Far more painful : I can't get the plugins to work. I installed three packages : digikamimageplugins, digikamplugins, libkipi0. I don't really know what the real "package" should be.
From what I understood, kipi plugins were dropped when 0.7 version was released, in favour of the digikam image plugins package.

Yet the configuration dialog in digikam displays a "kipi plugins" tab. And this tab states that "no kipi plugin could be found", even though I installed the package.

This is a major problem because those plugins were really useful (Batch rename and other simple image treatments...)

Did any of you succeed in making the plugins work?

If not, it seems the digikam package should be fixed! (and anyway, it should be updated, right now. 0.7.3 has been out for quite a while, and Digikam is one of the key-applications on a Kde desktop.)

---

### Post by defkewl on 2005-05-02
1) Try unmounting first before unplugging :) I have no problems so far.

---

### Post by subhankar on 2005-05-02
Hello,

I have a Canon Powershot A310 which isn't even being recognised!! I'm using Kubuntu (Hoary) and I have tried many ways manually, to no avail. /proc/bus/usb is always blank andd there's nothing in the logs that says that the camera has been detected. This camera did work on Arch Linux though and I don't have a clue here!! Please help, it's very frustrating  ](*,) 

Regards,
Subhankar

---

### Post by tristure on 2005-05-02
@defkewl:
I might be wrong, but i don't think my camera gets mounted ; I only plug it in, and then connect to it with the digikam menu option...
So either it's mounted automatocally, or digikam mounts it when connecting, or it isn't mounted at all.

Anyhow, how could I know where it's mounted?

---

### Post by tristure on 2005-05-03
[QUOTE=tristure]@defkewl:
I might be wrong, but i don't think my camera gets mounted ; I only plug it in, and then connect to it with the digikam menu option...
So either it's mounted automatocally, or digikam mounts it when connecting, or it isn't mounted at all.

Anyhow, how could I know where it's mounted?[/QUOTE]
 (up)
Does anyone have access to the image plugins within Digikam?
Could you just let me know if you have?

---

### Post by cwaldbieser on 2005-05-04
[QUOTE=tristure]@defkewl:
I might be wrong, but i don't think my camera gets mounted ; I only plug it in, and then connect to it with the digikam menu option...
So either it's mounted automatocally, or digikam mounts it when connecting, or it isn't mounted at all.

Anyhow, how could I know where it's mounted?[/QUOTE]

If you are getting pictures from it, it got mounted.  The way your PC sees your digital camera is the same way it sees a USB flash drive or pen drive.  This is how it works for most modern digital cameras you can get today (I had an old Olympus with a serial port interface a way back when...).  Anyway, if you plug your camera into a USB port, you can probably see it as a drive as well as using apps like digikam to see the pictures.

From konqueror, try typing something like:
```

camera://
```

in the address bar.  This should let you select your camera.  Otherwise, you might try looking in /media or /mnt to see if anything was mounted in one of those directories.

I don't normally have to unmount my camera when I unplug it.  However, I do have an mp3 player that didn't copy all my songs once when I unplugged it before unmounting...

For what it's worth, my usb devices normally get mounted on /dev/sdb1.

---

### Post by tristure on 2005-05-10
Well I'm pretty sure my camera isn't mounted.
At least nothing appears in /media or /mnt, no /dev/sdxx appears.

Now when I plug my camera for the first time, dmesg shows :

usb 1-2: new full speed USB device using uhci_hcd and address 2

When accessing it from digikam:
usb 1-2: usbfs: interface 0 claimed while 'digikam' sets config #1

When disconnecting it:
usb 1-2: USB disconnect, address 2

And if I plug it again :
usb 1-2: new full speed USB device using uhci_hcd and address 3

Then I can't access it from digikam anymore. It seems related to the address (2 the first time and 3 the second)... But I can't see what to do.

---

### Post by tristure on 2005-05-10
Then again, the most annoying problem I have with Digikam concerns the plugins (supposedly the "kipi" plugins).

I installed digikam, and all the packages concerning kipi or digikam I could find : digikamplugins, digikamimageplugins, libkipi0, libkipi0-dev

And I still haven't any plugin available.

Could any of you check this out?
You just have to open digikam, then look at menu Tools--> Batch Process ->>??
My Batch process menu is empty, it should not be.
And then open the configuration dialog and check the "kipi plugins" part. Mine shows 0 plugins found, which is not really normal.

If any of you could spend some seconds to check those two things and report it here, I'd be very grateful, because it could help me determine if the problem is only on my box, or if the ubuntu digikam package is corrupted... (then I could file a bug report).

Thanks!

---

### Post by James Wilford on 2005-05-11
[QUOTE=tristure]Then again, the most annoying problem I have with Digikam concerns the plugins (supposedly the "kipi" plugins).

I installed digikam, and all the packages concerning kipi or digikam I could find : digikamplugins, digikamimageplugins, libkipi0, libkipi0-dev

And I still haven't any plugin available.

Could any of you check this out?
You just have to open digikam, then look at menu Tools--> Batch Process ->>??
My Batch process menu is empty, it should not be.
And then open the configuration dialog and check the "kipi plugins" part. Mine shows 0 plugins found, which is not really normal.

If any of you could spend some seconds to check those two things and report it here, I'd be very grateful, because it could help me determine if the problem is only on my box, or if the ubuntu digikam package is corrupted... (then I could file a bug report).

Thanks![/QUOTE]

For what its worth, I just installed Digikam and I have the same problem with missing plugins. If you find a solution, please post it here!

Cheers

---

### Post by tristure on 2005-05-11
Thanks for your answer.
Did you install the various plugins packages?
I don't which one is supposed to be the correct one, but you could try :
digikamplugins
digikamimageplugins
libkipi0
libkipi0-dev

If you install these and still have no luck, I think we can consider that the packages themselves are buggy.

---

### Post by James Wilford on 2005-05-11
[QUOTE=tristure]Thanks for your answer.
Did you install the various plugins packages?
I don't which one is supposed to be the correct one, but you could try :
digikamplugins
digikamimageplugins
libkipi0
libkipi0-dev

If you install these and still have no luck, I think we can consider that the packages themselves are buggy.[/QUOTE]

I had all those packages, except libkipi0-dev which I've just installed, but that made no difference, as I expected - I think its only needed for compiling software against kipi.

Looks like there's a bug, unless we are missing something...  :-?

---

### Post by joni on 2005-05-11
Subhankar: You can find a list of the supported cameras by libgphoto2, which digikam uses at:

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php) 

Your Canon Powershot A310 is there, but it says PTP mode (I don't know what that is...).

So, I guess it should work.

---

### Post by cwaldbieser on 2005-05-12
I finally got around to trying out some experiments with my Cannon Powershot A70.  When I plug it in, I don't get any new devices, either.  However, if I try

```
$ lsusb
```

at the console, I can see it.  I can also access it like drive if I do

```
camera:/
```

in konqueror.  Digikam lets me access it as well, though in the setup for adding the camera, I notice there are some greyed out options for me.  Are you able to change any of these?

You are probably right about the changing address numbers being the problem, though I am not sure what you can do about that.  If you remove the camera from digikam and re-add it, can you see it again?

---

### Post by poofyhairguy on 2005-05-12
try starting digikam this way and see if it works. in the run program place put:

gksudo digikam

fixes the problem for me.

EDIT: make sure gksudo is installed first!!!

---

### Post by dodger on 2005-06-06
[QUOTE=tristure]Hi,

I experience some annoying problems with digikam, did anyone have the same problems?

1) (not very serious, but still a little pain) When accessing a digital camera, connexion only succeeds the first time you plug it in.
If you unplug it, then plug it again in the same KDE session, the connexion won't work. I have to reboot in order to make it work again.
Well, I rarely have to plug my camera multiple times during the same session, but it should be fixed anyway.

2) Far more painful : I can't get the plugins to work. I installed three packages : digikamimageplugins, digikamplugins, libkipi0. I don't really know what the real "package" should be.
From what I understood, kipi plugins were dropped when 0.7 version was released, in favour of the digikam image plugins package.

Yet the configuration dialog in digikam displays a "kipi plugins" tab. And this tab states that "no kipi plugin could be found", even though I installed the package.

This is a major problem because those plugins were really useful (Batch rename and other simple image treatments...)

Did any of you succeed in making the plugins work?

If not, it seems the digikam package should be fixed! (and anyway, it should be updated, right now. 0.7.3 has been out for quite a while, and Digikam is one of the key-applications on a Kde desktop.)[/QUOTE]
 concerning the kipi-plugins, have a look here:

[http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php](http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php)

which will tell you to add this to your sources list:

deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./

you can then do:

apt-get install kipi-plugins 

and should be fine

---

