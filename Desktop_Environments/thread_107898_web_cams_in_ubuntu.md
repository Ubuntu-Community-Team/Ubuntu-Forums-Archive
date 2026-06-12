---
title: "web cams in ubuntu"
date: 2005-12-24
forum: Desktop Environments
---

### Post by shadowman on 2005-12-24
Hi all,

I am not much of a multimedia person but with my daughter away at med school I thought a web cam would be fun.

Can anyone recommend one for using with ubuntu and the related application for it?

Thanks,

John Little
Network Engineer
Hendricks Regional Health

---

### Post by anil_robo on 2005-12-25
1. First, install camorama by opening a terminal (applications--> Accessories-->Terminal) and typing the following command:
```
sudo  apt-get install camorama
``` press enter, type your password and press enter again.
Camorama should be installed in Applications-->Graphics-->Camorama.
2. Now make sure you have saved any documents you're working on, because we're heading for a possible crash: Plug your webcam in the USB port and start camorama.
3. If all goes well, your webcam will start and camorama will show you the live video.
Otherwise your system will hang and you'll have to reboot. If this is the case, you can follow this excellent guide here: [http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")
This guide is pretty simple to follow: Just copy and paste commands from it to the terminal, and you'll be done! :)

For video chatting, you have to use gnome-meeting (Applications--> Internet--> GnomeMeeting). This is installed by default. How to use GnomeMeeting? I don't know! You find out and tell me! :)

I have a "Logitech Quickcam Webcam" and it works well with camorama. However, I dont know how to use it with gnomemeeting, so this is pretty much just a toy as of now. ;)

---

### Post by shadowman on 2005-12-26
anil_robo

Thanks!  That's exactly the information that I was looking for! :D

---

### Post by jbraum on 2006-01-12
awesome.  Followed the code and bomb there she goes.  Thanks

---

### Post by chele on 2006-01-14
Don't forget this [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") page which has an application simplifying the installation of additional webcam drivers. Worked great for the Creative webcam I picked up at the local computer store.

---

### Post by Brando569 on 2006-01-19
whenever i click 'take picture' it says that it cant create the directory ~/Webcam_pictures ive even ran it via sudo and still got the same error....

---

### Post by ftmichael on 2007-12-23
> whenever i click 'take picture' it says that it cant create the directory ~/Webcam_pictures ive even ran it via sudo and still got the same error....

Try creating the directory manually first.  Alternatively, go to Edit->Preferences, click the Local Capture tab, and change the directory it automatically saves to.

Michael

---

### Post by IanLeith on 2007-12-23
WOW ...was that easy..
Thanks..
Ian:popcorn:


Can anyone recommend one for using with ubuntu and the related application for it?

Thanks,

John Little
Network Engineer
Hendricks Regional Health[/QUOTE]

---

### Post by LaRoza on 2007-12-23
> **IanLeith said:**
> 
Can anyone recommend one for using with ubuntu and the related application for it?



[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Kopete

---

