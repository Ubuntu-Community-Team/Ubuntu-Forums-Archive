---
title: "help with the newbie experience"
date: 2006-01-06
forum: General Help
---

### Post by lava on 2006-01-06
Hi, I'm a newbie to kubuntu. With all the talk of Vista i wanted to check out if there was anything in linux that was just as cool, and after doing some research I settled on kubuntu. I still don't know what's better, gnome or KDE, but it seemed like there was more support for KDE out there, so that's what I settled on. So far, the experience has been painful. I'm an advanced user of windows, and if I have a configuration problem there, I can easily figure it out. It hasn't been that way with kubuntu so far, and it's getting frustrating. 

These are the thigns that I'm trying to get done:

1. Set up my second monitor. I have an ATI All-In-Wonder card, which is multihead, and it's making me seriously uncomfortable being restricted to one monitor.

2. Figure out how to mount an NTFS partition. I'm dual booting right now. All my music and important documents are on NTFS partitions. I would like to be able to listen to my music collection while I'm working on linux. 

3. Figure out how to play streams on amaroK. For some reason, whenever I try to play a stream it buffers to 100 percent and then it restarts buffering... over and over and over. I need my KCRW. 

If you could help me that would be great. ;) I'm still doing my research on my own and I'm looking throught this forum to see if any of these questions have been answered already. 

Thanks.

---

### Post by Aphorism on 2006-01-06
While the forums are a wonderful place for help, try starting with the ubuntu wiki.

And if you discover something new, add it to the wiki so the knowledge grows.

[http://wiki.ubuntu.com](http://wiki.ubuntu.com)

---

### Post by flight_master on 2006-01-06
Hello,

Believe me, Linux is like starting from square one! (Remember your first day on Windows? ;))

Ok, let's get to it, shall we?

> 1. Set up my second monitor. I have an ATI All-In-Wonder card, which is multihead, and it's making me seriously uncomfortable being restricted to one monitor. 

You'll need the fglrx Drivers for ATI cards (I have the same card!) You can use apt-get to install the drivers, but I recommend Synaptic. Here's the howto:
[Older, Easier to install Drivers] [http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)
[Latest, Harder to install Drivers] [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

> 
2. Figure out how to mount an NTFS partition. I'm dual booting right now. All my music and important documents are on NTFS partitions. I would like to be able to listen to my music collection while I'm working on linux.

Open a Konsole (Kmenu -> Run -> Type in 'konsole' without quotes).
type in the following line:
```
sudo mount
```
Make sure to enter your password at the prompt. You can then find your hard-drives mounted under /media/, which you can access through any application, such as Konqueror.
> 
3. Figure out how to play streams on amaroK. For some reason, whenever I try to play a stream it buffers to 100 percent and then it restarts buffering... over and over and over. I need my KCRW.
What version of amaroK are you using? ;)

Regards,
Christian

---

### Post by lava on 2006-01-06
sweet, I got pretty quick responses. I'm currently running amarok 1.3.1. What I'm trying out is this... I click on the playlists tab, and navigate to Radio Streams>Cool Streams. I double click on one of the streams (groove salad for example). The playlist populates with feeds. Nothing happens, so I'll double click one of the feeds and amaroK will download the current song information, but it just keeps buffering and doesn't play anything.

---

### Post by lava on 2006-01-06
oh and I tried sudo mount. nothing new showed up under media, This is what I got on the console after I typed the command:

/dev/hdc3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

I have 3 disks. two of them are just single NTFS partitions, and the third one is two ntfs and the linux partition.

---

### Post by flight_master on 2006-01-06
Lava,

This is (K)Ubuntu... Opensource support is almost instant :D

Regarding your hard-drives; can you post the output of the following?

```

cd /media; ls;

```

Regarding AmaroK,
This might be a problem with the G-streamer engine, it has issues. Have a look here: [http://ubuntuforums.org/showthread.php?t=82845](http://ubuntuforums.org/showthread.php?t=82845) I highly recommend the Xine engine, as I've used it on MDK before. Arts seems to work very well on Kubuntu too, though.


Regards,
Christian

---

### Post by lava on 2006-01-06
I fixed my audio issue. I remembered that when I was researching kubuntu one of the faqs was "how do I play MP3s" and it struck me as weird at the time. But I went back and followed the instructions and mp3s and audio streams started working fine. The line was "Install the akode-mpeg and gstreamer0.8-mad packages from the universe repository and killall artsd to restart the sound server." It took me a little while to figure out what the universe repository was. I also took me a while to figure out how to install synaptic, but that's now done.

Regarding the mounting issues. after I do 
> 
sudo mount
cd /media
ls

I only get:
> cdrom cdrom0 floppy floppy0

and by the way, my video card is an ATI all in wonder 9600, is that the card you have?

Thanks,

---

### Post by flight_master on 2006-01-06
Hi again,


Yes - that's why I told you to switch the Sound-engine ;) Gstreamer, as packaged by Kubuntu, doesn't support MP3 playback.

How are these drives configured? Are they a RAID array, or just connected to the motherboard with an IDE cable? 

Yes, I have an ATI All-In-Wonder Pro 9600 Video card. Contrary to what most people say, they work very well in Linux :D


Regards,
Christian

---

### Post by lava on 2006-01-06
the drives are just connected to the motherboard via IDE cables.

---

### Post by lava on 2006-01-06
actually, I just figured out how to mount from here: 
[http://kudos.berlios.de/kf/kisimlar/windows.html#hddmntman](http://kudos.berlios.de/kf/kisimlar/windows.html#hddmntman)

all I have left now is the ATI driver. I'm halfway through that.

---

### Post by flight_master on 2006-01-06
That's interesting; Normally, k/ubuntu should detect partitions on install, so you don't need to mount each by itself. Glad you found the answer though!

Regards,
Christian

---

