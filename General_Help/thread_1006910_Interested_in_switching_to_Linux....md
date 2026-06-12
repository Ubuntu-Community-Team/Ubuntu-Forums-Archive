---
title: "Interested in switching to Linux..."
date: 2008-12-09
forum: General Help
---

### Post by cdahmedeh on 2008-12-09
Hello,

I'm currently interesting into switching to Linux. I've tried a few distributions and I'm interesting in Ubuntu the most. I know that Linux is an OS that needs time and patience, but that does not bother me as I know the end result is worth it. I'm not scared of command line or anything like that, I have lots of experience with computers, drivers, etc. Also, according to Wine AppDB all the games I usually play are compatible with WINE. However, I have many questions :

1. What is the recommend way of formatting my hard disk ? On my current system with Windows, I have a small partition of 30GB for the OS and the Programs and another 120GB partition for Games, Movies, etc. Also, is it recommend to switch to the Linux partition system, or I can conserve the NTFS file system on my second partition (120 GB one) in case I want to go back as it has all my backup files.
2. How well does Ubuntu support the XPS m1530 ? Does it support the webcam and the fingerprint reader ?
3. Does Ubuntu support a Avermedia NanoExpress TV Tuner. Lets say the driver isn't availible, is it possible to use a wrapper to make the original windows driver to work in Linux so that I can watch TV on it ?
4. How is Bluetooth support in Linux. I have a hacked driver for my Sixaxis that allows me to connect it to the PC so I can play games. I've heard its easier to do so in Linux since you can modify the bluetooth behavior. 
5. How is the battery management in Linux ? Can I control things like CPU Speed in order to increase battery life and things like that ? What programs can monitor CPU Speed and does it support Intel's SpeedStep ?
6. Is it recommended to keep a Windows Partition. My switch seems to be permanent, since all the games I play (pretty old ones) work fine in WINE and I'm not interesting in the new games. Also, I know that Virtual Machines and WINE can run applications that have low specifitions incase I need some specific program for a project.
7. Does Linux support Packet Injection for WIFI networks with an Intel 4965AGN ?
8. I've noticed that Linux takes time to boot up on the Live CD. How fast does it boot on a 7200 RPM Hard Drive with a 2.2 GHz processor ? Is there anyway to increase boot time ?
9. Finaly, what customization options do I have in the UI ? Is it possible to change the boot screen ? Can I install different skins and things like that. Compiz Fusion seems very interesting.

Thanks. I really can't wait to make the switch and get over with this Windows. I really feel like Linux will let me take control of my computer. I really love how the Console is accessible with a simple key command !

---

### Post by dannytatom on 2008-12-09
> **cdahmedeh said:**
> 
9. Finaly, what customization options do I have in the UI ? Is it possible to change the boot screen ? Can I install different skins and things like that. Compiz Fusion seems very interesting.

Unfortunately, all I can answer is #9 (don't know enough about the others, and wouldn't want to give you a wrong answer).

**As for the answer,** you can customize pretty much every part of the UI.  For themes/icons/etc you can check out [http://gnome-look.org](http://gnome-look.org) or xfce-look and kde-look depending on what desktop environment you use (i'm assuming gnome).  And if you can't find something that works for ya, you can always make your own. :)

& welcome to the forums. :)

---

### Post by cdahmedeh on 2008-12-09
Thanks for you reply. Don't worry, I'm not expecting all the asnwers in one post, but I looked at your website and it looks very impressive.

---

### Post by snova on 2008-12-09
> **cdahmedeh said:**
> 1. What is the recommend way of formatting my hard disk ? On my current system with Windows, I have a small partition of 30GB for the OS and the Programs and another 120GB partition for Games, Movies, etc. Also, is it recommend to switch to the Linux partition system, or I can conserve the NTFS file system on my second partition (120 GB one) in case I want to go back as it has all my backup files.

How about a dual boot?

> 5. How is the battery management in Linux ? Can I control things like CPU Speed in order to increase battery life and things like that ? What programs can monitor CPU Speed and does it support Intel's SpeedStep ?

Yes, I think so. There's a little thing in my systray that I can change, but as I've never used it, I have no idea how good it is. Or what SpeedStep is.

> 6. Is it recommended to keep a Windows Partition. My switch seems to be permanent, since all the games I play (pretty old ones) work fine in WINE and I'm not interesting in the new games. Also, I know that Virtual Machines and WINE can run applications that have low specifitions incase I need some specific program for a project.

I suggest you keep the existing one for a while. At least until you know for sure that you don't need it any longer.

> 8. I've noticed that Linux takes time to boot up on the Live CD. How fast does it boot on a 7200 RPM Hard Drive with a 2.2 GHz processor ? Is there anyway to increase boot time ?

The live CD is slow because it has to read everything off a disk (in addition, decompress it). It's much faster normally.

> 9. Finaly, what customization options do I have in the UI ? Is it possible to change the boot screen ? Can I install different skins and things like that. Compiz Fusion seems very interesting.

Many.

---

### Post by LoneWolfJack on 2008-12-09
> 1. What is the recommend way of formatting my hard disk ? On my current system with Windows, I have a small partition of 30GB for the OS and the Programs and another 120GB partition for Games, Movies, etc. Also, is it recommend to switch to the Linux partition system, or I can conserve the NTFS file system on my second partition (120 GB one) in case I want to go back as it has all my backup files.

When you install ubuntu, it will give you the option to move partition sizes back and forth, so you can keep the NTFS partition if you feel like it. NEVER EVER rely on any partitioning system to not damage your backup files on another partition though. ALWAYS do a hard backup (other drive, cd, dvd, etc.)

> 2. How well does Ubuntu support the XPS m1530 ? Does it support the webcam and the fingerprint reader ?

you'd better try to get an answer for that in a seperate thread of by using google. the more exotic your hardware, the less chances it will work in linux though.

> 3. Does Ubuntu support a Avermedia NanoExpress TV Tuner. Lets say the driver isn't availible, is it possible to use a wrapper to make the original windows driver to work in Linux so that I can watch TV on it ?

if there is no driver at all, there is for sure some wrapper that will enable you to use the basic features at least. if that isn't enough, you can consider running windows in a VM.

> 4. How is Bluetooth support in Linux. I have a hacked driver for my Sixaxis that allows me to connect it to the PC so I can play games. I've heard its easier to do so in Linux since you can modify the bluetooth behavior.

out of the box the support is so-so... some things work, some don't. you can't fiddle around with the configs all day though.

> 5. How is the battery management in Linux ? Can I control things like CPU Speed in order to increase battery life and things like that ? What programs can monitor CPU Speed and does it support Intel's SpeedStep ?

somewhere in this forums it says battery management got way better in intrepid than in was in gutsy... can't really judge that as I don't need 
it.

> 6. Is it recommended to keep a Windows Partition. My switch seems to be permanent, since all the games I play (pretty old ones) work fine in WINE and I'm not interesting in the new games. Also, I know that Virtual Machines and WINE can run applications that have low specifitions incase I need some specific program for a project.

sounds like you don't need a windows partition

> 7. Does Linux support Packet Injection for WIFI networks with an Intel 4965AGN ?

that's pretty in depth and should go to a separate thread if you expect someone to answer that question :)

> 8. I've noticed that Linux takes time to boot up on the Live CD. How fast does it boot on a 7200 RPM Hard Drive with a 2.2 GHz processor ? Is there anyway to increase boot time ?

I find gutsy and intrepid both pretty slow to load, but faster bootup is on the todo list for jaunty (coming april)

> 9. Finaly, what customization options do I have in the UI ? Is it possible to change the boot screen ? Can I install different skins and things like that. Compiz Fusion seems very interesting.

the boot screen can be changed (afaik). the UI is quite flexible... there are plenty of window managers around if you don't like metacity. I've even seen one that looks like the new fedora 10 desktop, but didn't have time to test it yet.

---

### Post by fenian on 2008-12-09
1-Here is how I like to partition for ubuntu...

20 GB  for OS formatted as ext3 and mounted at /
10-20 GB for Home directory formatted as ext3 and mounted at /home 
the rest as storage formatted as XFS 

2-I'm not sure but there is a [thread here about the XPS]("http://ubuntuforums.org/showthread.php?t=652364").

3-Not sure check linuxtv.org.


4-I don't know.

5-I don't know.

6-To start out I would probably keep a windows partition just in case.If you don't ever use it it's not a problem just a bit of wasted space but if you do need windows at some point and it's not installed it can be a bit of a hassle to install it after Ubuntu.

7-I don'yt know

8-My boot time is about 35 seconds,expect between 35 seconds and 1 minute,if you search these forums for 'speed up boot time' there are some threads on this.

9-Linux in my experience is far more customizable than any other OS        I have used,check gnome-look.org for themes,icons and other things to help customize your Ubuntu.

---

### Post by cdahmedeh on 2008-12-09
Thank you for your answers, let me just check what has been answered

1. OK I will back up all my files on external hard drive. I will then reserve then entire hard drive to Linux.
2. I found some website about the support of this laptop. Currently, almost all of its components are supported. That is good.
3. I don't know about this one yet.
4. Sixaxis works on Linux and there is a website dedicated to that functions and it shows all the procedures. 
5. Still unsure about this question. I want to know how to monitor my CPU Speed, and how to change it. Like in RMClock so I can manage battery life.
6. Virtual Machine Sounds like a good idea.
7. Just checked, Linux does support Packet Injection for WIFI networks with an Intel 4965AGN 
8. 30 secs - 1 mins is already much better than my current XP Installation.
9. Possibilities look infinite....

Anyways, I will take a look at Linux next week and install it on my laptop. It feels I will finally be able to use my hardware for a long time. Windows 7 isn't taking the route I'm interested in, the definition of user-friendly to me isn't the OS doing the jobs for you, its about you being to control your hardware....

---

### Post by heapy on 2008-12-10
now then boss, i am in a similar situation to you. I have almost the same spec xps, and am new to linux. What version of ubuntu are you considering? tonight I am to download either 8.10, or 8.04.1.. (just to add to the confusion dell have an .iso of ubuntu!) Sorry I dont have the answers to your questions. maybe try and run live and see what works and doesn't? tomorrow i get a hdd from dell, so i can finially install linux.. x

edit, found the dell iso
[http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)

man im so confused, what version! : )

---

### Post by compman25 on 2008-12-10
> **heapy said:**
> now then boss, i am in a similar situation to you. I have almost the same spec xps, and am new to linux. What version of ubuntu are you considering? tonight I am to download either 8.10, or 8.04.1.. (just to add to the confusion dell have an .iso of ubuntu!) Sorry I dont have the answers to your questions. maybe try and run live and see what works and doesn't? tomorrow i get a hdd from dell, so i can finially install linux.. x

edit, found the dell iso
[http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)

man im so confused, what version! : )

Try Ubuntu first by installing with Wubi, then if you like Ubuntu install from the cd. If you don't like it you just uninstall Wubi from Windows Add/Remove

---

### Post by jerome1232 on 2008-12-10
> 5. Still unsure about this question. I want to know how to monitor my CPU Speed, and how to change it. Like in RMClock so I can manage battery life.

For me personally Ubuntu Hardy on **my** Laptop does a better job of this than vista does.

Under vista I have to goto my system tray and manually choose the performance level I want. There's three settings.

Under Ubuntu, When I plug in to power everything pop's into high performance mode (lights brighten clock speeds scales up etc..)

When I'm on battery it auto dims the lcd lights and scales the cpu down. I like it automatic this way although I haven't found much that can be configured other than the dimming/brightening of lcd lights.

---

### Post by bruce2000 on 2008-12-10
> **heapy said:**
>  
man im so confused, what version! : )


8.10 is the latest version and has better support for wifi whereas 8.04 has long term support (3 years instead of 18 months)

---

### Post by ubuntu27 on 2008-12-10
> **cdahmedeh said:**
> Hello,


1. What is the recommend way of formatting my hard disk ? On my current system with Windows, I have a small partition of 30GB for the OS and the Programs and another 120GB partition for Games, Movies, etc. Also, is it recommend to switch to the Linux partition system, or I can conserve the NTFS file system on my second partition (120 GB one) in case I want to go back as it has all my backup files.


GNU/Linux supports many FileSystems sych as NTFS, FAT32, FAT, Ext2, **Ext3**, Ext4, ReiserFS, XFS, etc. 

It is highly recommended that you use **Ext3**. When you are about to partition the drive, don't forget to Choose Ext3 as the FileSystem.

Also, I recommend you to read [How to Plan your Partitions]("http://www.psychocats.net/ubuntu/partitioning") by [aysiu]("http://ubuntuforums.org/member.php?u=21941").

[That guide]("http://www.psychocats.net/ubuntu/partitioning") give you a rundown on the advantages that certain partitioning schemes have over others. 


[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/")

---

### Post by falkTX on 2008-12-12
> **cdahmedeh said:**
> Hello,

4. How is Bluetooth support in Linux. I have a hacked driver for my Sixaxis that allows me to connect it to the PC so I can play games. I've heard its easier to do so in Linux since you can modify the bluetooth behavior. 


I'm working in an application to setup sixaxis in Ubuntu. It works fine now in bluetooth mode. Now I'm trying to make a GUI to setup sixaxis as a mouse and keyboard (it requires some work).

Check for details:
[http://ubuntuforums.org/showthread.php?t=973112](http://ubuntuforums.org/showthread.php?t=973112)

---

