---
title: "Olympus d580 zoom camera trouble"
date: 2006-01-10
forum: General Help
---

### Post by Jott on 2006-01-10
Hi,

wow, this is the first time I've ever posted anything in a forum of any kind.  hope I'm not puting it in the wrong place or anything.

anyway, I'm hoping someone can help with this digital camera problem I'm having.  I'm migrating from Windows, and have very little idea what I'm doing when it comes to setting up Ubuntu.  With some help from a friend and from reading posts in this forum, I've got almost everything working.  One of the few remailing problems is my camera.  It's an Olympus camedia D580 zoom.  The wiki sais it should just work, but it just doesn't.  I've tried everything I can find on the forums, I've tried mounting it manually;  I think ubuntu just doesn't see the camera.  My USB jump drive works fine; the camera and card work fine in windows, just no luck in ubuntu.  Any suggestions? 

Thanks!

---

### Post by eqisow on 2006-01-10
Are you trying to use a card reader or is the camera plugged in directly via USB? Card readers have very bad support in linux due to various patent issues and what-not. (somebody correct me if I'm wrong) If you are using USB however, I'm afraid I don't have much help to offer.

---

### Post by Jott on 2006-01-10
Thanks for the reply -

I'm trying to plug the camera in directly via usb.

---

### Post by zoiks on 2006-01-10
What shows up if you go to the command line and type "lsusb" while the camera is plugged in?

Well, there are two basic ways digital cameras are accessed in linux.

1) If the camera is acting as a simple USB mass storage device (or if you can get it into this mode), then just plugging it in to a USB port should work.  Either ubuntu will automount the data to a directory in /media, or you can manually mount it and access the data.

2) If the camera does not act as a simple USB storage device, then the other bet would be gphoto2 (libgphoto2).  It has commands that allow you to just copy all of the photos onto your hard drive, for example.  Not all of the remaining cameras will work with this.  A list of supported cameras is here

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Your camera is not on the list, so it's not officially supported.  If it were me, I'd give it a try anyway and see what happens.

If it doesn't work, I'd contact Olympus support and see what they offer.  They may have a solution.  If not, it's at least worth giving them a hard time for not supporting published standards.

---

### Post by Jott on 2006-01-10
*[QUOTE=zoiks]What shows up if you go to the command line and type "lsusb" while the camera is plugged in?*
[/QUOTE]
I get:
Bus 001 Device 001: ID 0000:0000
> 
*1) If the camera is acting as a simple USB mass storage device (or if you can get it into this mode), then just plugging it in to a USB port should work.  Either ubuntu will automount the data to a directory in /media, or you can manually mount it and access the data.*

unfortunately, this doesn't work.
> 
[I]2) If the camera does not act as a simple USB storage device, then the other bet would be gphoto2 (libgphoto2).  It has commands that allow you to just copy all of the photos onto your hard drive, for example.  Not all of the remaining cameras will work with this.  A list of supported cameras is here

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Your camera is not on the list, so it's not officially supported.  If it were me, I'd give it a try anyway and see what happens.[/I]

I'll try that, though I'm afraid if the OS doesn't see the camera plugged in to the usb I may be out of luck.
> 
[I]
If it doesn't work, I'd contact Olympus support and see what they offer.  They may have a solution.  If not, it's at least worth giving them a hard time for not supporting published standards.[/I]

Worth a shot! Thanks.

---

### Post by Jott on 2006-01-11
any other ideas?

---

### Post by Jott on 2006-03-21
Upgraded to dapper and the problem went away!  camera now mounts as a USB mass storage device with no problem at all.
!

---

