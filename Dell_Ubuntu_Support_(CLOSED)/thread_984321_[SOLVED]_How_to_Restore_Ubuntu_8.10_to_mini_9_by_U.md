---
title: "[SOLVED] How to Restore Ubuntu 8.10 to mini 9 by USB?"
date: 2008-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by suprmatt on 2008-11-16
EDIT:  For whatever reason I mistyped the version of Ubuntu that I need to restore...8.04 is what is included on the Dell restore disc that I have.  That is what I need to restore to the mini 9 via usb.

I have a mini9 4GB model that I installed win xp on via a usb thumb drive.  After the install, there is less than 200MB free space on the ssd.  I have the Ubuntu 8.04 restore disc that came with the mini and I would like to restore it to the state it was in when I received it.  The only problem is that I do not have an external disc drive, and for the life of me I cannot figure out how to get restore it using a flash drive.  Does anyone have any ideas?  Right now I have it running 8.10, but it is missing all the codecs, media playback and the shortcut bar that came installed.  Any help would be appreciated.

---

### Post by notwen on 2008-11-17
[Unetbootin]("http://unetbootin.sourceforge.net/") will do exactly what you're wanting. =]  It can download certain distro installs for you and can also use local isos as a source.  Hope this helps.  =]

---

### Post by suprmatt on 2008-11-17
Unetbootin does not work with the Iso I created of the dell restore disc.  I would like to restore the customized ubuntu mini os that came preinstalled on the mini without having to purchase an external cd drive.  There must be a way to restore the image from usb media.  Thanks for your help.  I tried unetbootin yesterday, but tried it again thinking I screwed up somehow.  I even created another iso image thinking I screwed that up somehow.  The dell restore disc is just that...a restore disc.  It isn't a regular ubuntu iso, I think that may be why it won't work.

---

### Post by starcannon on 2008-11-17
**Please Help me seed by downloading and leaving it up to seed using this link:**
[http://linuxtracker.org/index.php?page=torrent-details&id=3d86a374bc7c287df78e297b1ce5cb648a857c4b](http://linuxtracker.org/index.php?page=torrent-details&id=3d86a374bc7c287df78e297b1ce5cb648a857c4b)

I'm on a slow connection of only 1mb and it will be on and off available, I will leave mine running as much as possible until 10 other seeders are rolling, I will even move this seed to a more stable connection this week sometime, or I would like to help seed someone else's Official Dell Restore .img file (pm me if you have this same exact torrent rolling, I'll drop mine and join your efforts.)

I'm pretty sure I saw someone make a bootable restore disk on the official dell forums, I'll dig up that link for you if I can find it again, and edit it into this post.

**Found it, here it is!**
[http://en.community.dell.com/forums/t/19233531.aspx](http://en.community.dell.com/forums/t/19233531.aspx)

Read through that post, it is marked as solved at the dell forums.
> 
Re: Make a bootable USB key of the Dell Ubuntu iso image for Mini 9 PoorPoorFairFairAverageAverageGoodGoodExcellentExcellent
27 Oct 2008 10:49PM

I finally got the img that is posted on the Dell support site to run from a USB key.

 

There are two ways to do this. Since its an image NOT an iso you can use the "dd" command.

 

It would look like this:

sudo dd if=/path_to_restore_image/restore_image.img of=/path_to_your_USB_key bs=1024 (such as /dev/sdc/)

 

The other way is to download image-writer [http://ppa.launchpad.net/ogra/ubuntu/po](http://ppa.launchpad.net/ogra/ubuntu/po) ... a1_all.deb

 

Image-writer is a graphical front end for dd. Look for it in Applications/Accessories.

 

I booted off the USB key to a text based screen advising me that if I press enter the system would be over written with the restore image. The system was restored and it asked you to remove the USB key. Then the system was rebooted.

 

Be careful. If you press enter the SSD gets overwritten with the restore image.

 

I went through the initial set up and after another reboot it was up and running the Dell version of Ubuntu Hardy.
Message Edited by onefish2 on 10-28-2008 01:04 AM
The Img file is available here: [http://ftp.us.dell.com/OS/Inspiron_910_Ubuntu_A00.img](http://ftp.us.dell.com/OS/Inspiron_910_Ubuntu_A00.img)
Lets get that thing seeded, its currently rather a bit of a unicorn.

GL and keep it fun

---

### Post by C.S.Cameron on 2008-11-17
Not sure about the Mini but the EEE includes a utility CD that can be used on a second computer to make a restore USB flash drive.

---

### Post by shiningkenmonster on 2008-11-20
i am trying do to the same thing. I want to do a system restore on a usb flash drive. but i've called the dell tech support with no help. they couldn,t give me a link.

the other guy above me has a link to download the image.

if i download that 1GB image. can you run that with unetbootin? would i need to do anything to the usb flash drive? such as usb-imagewriter? or do i not need to do anything and it'll just work?

---

### Post by leegwebb on 2008-12-11
Sorry, this is no longer a solved issue, as none of the links to the img file in the thread are working now.  Does anyone have an update.  I am on chat with Dell right now, and they don't really understand what I need.  They keep referring me to the Gutsy ISO for the Inspiron 1425 and other larger laptops that they sell with Ubuntu.  It's very frustrating, because they shipped the Mini with a generic Hardy CD and a booklet for the Windows version.

---

### Post by JRSinOK on 2009-01-05
I am running into the same issue.  Can anyone post a link of the Hardy 8.04 ISO image that dell shipped the mini 9's with?

---

### Post by leegwebb on 2009-01-05
OK, I did get my mini restored.  First, you want an .img file rather than an .iso because the mini doesn't have an optical drive.

The instructions at [http://en.community.dell.com/forums/p/19233531/19379737.aspx](http://en.community.dell.com/forums/p/19233531/19379737.aspx) work.  I used the second method: image-writer.  It was already on my Ubuntu Hardy system, but you could install it as described in the post.  From there it is just as easy as described.

However, the ftp link to the .img file referred to in this post does NOT work.  After some searching, I eventually found a torrent that worked, I think at isohunt.com.  just try searching da interwebs for Inspiron_910_Ubuntu_A00.img and you will eventually find a working torrent.  Download it, make a bootable USB stick using image-writer, and you will be on your way.  Don't forget to backup any of your own files first, because this method is a complete overwrite of the SSD.

---

### Post by carleton on 2009-02-19
I got the img onto my usb stick and booted it up, but after a few screens of loading it goes into a loop of "Sleeping for 5 seconds" then checking device /dev/sda through sdd for installation source then sleeping again

any help would be appreciated!

---

### Post by delboy1 on 2009-02-19
The only way I could get the Dell version of 8.04 restored on to my mini was by borrowing an external dvd drive. The usb method just wouldn't work althpough I have been able to install 8.10 via usb with no problems

---

### Post by carleton on 2009-02-19
did you just make a Startup usb disk?

---

### Post by armandh on 2009-02-19
I have installed several OS' to my mini finally ending with a xp/8.10 dual boot in the 16 G e-hdd and I have put Ubuntu live on a USB memory stick.

but

the custom dell 8.04 is bigger and on a DVD so I got a USB case and put in a spare from the parts bin. 

PS many USB Hdd have a regular eide ribbon cable and can be hooked to a spare or borrowed dvd drive

---

