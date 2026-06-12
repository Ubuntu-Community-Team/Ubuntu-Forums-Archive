---
title: "amarok mtp support in gnome? Help needed"
date: 2006-10-07
forum: Desktop Environments
---

### Post by NESFreak on 2006-10-07
I have mtp and gnomad working, but I'd like to sync from Amarok to my zen sleek photo. Whenever I try to do an autodetect from the settings menu it tells me that it hasn't found any devises and advices  me to "dcop kded mediamanager fullList" but that gives me "call failed" as reply? Is there a kde program missing? btw I'm not willing to do a full kubuntu install.
--------------------------
found out I don't have the mtp plugin. Where is it? I have the latest amarok version from the repository from the official amarok site.


NESFreak

edit: see [http://ubuntuforums.org/showpost.php?p=2031283&postcount=18](http://ubuntuforums.org/showpost.php?p=2031283&postcount=18) for the files you need to get MTP Support in Amarok without compiling or anything difficult.

edit:THEY APPEAR TO BE BROKEN WITH AMAROK 1.4.5

just download the zip file and run this command. Add your mtp device in the amarok settings and it just works. All thanks to imopenO:) .
```
sudo unzip amarok_mtp.zip -d /
```

[direct link to the archive]("http://ubuntuforums.org/attachment.php?attachmentid=23375&d=1169145323")
btw they are for Amarok 1.44 (don't know if they work with older versions, though they appear to be broken with the SVN version (which you compile yourself anyway))
see [this post]("http://www.ubuntuforums.org/showpost.php?p=2039929&postcount=27") for if your device isn't supported by libmtp (for a full list enter "mtp-hotplug" on the commandline).

---

### Post by NESFreak on 2006-10-07
lol you need to compile it in. Wich isn't done because ubuntu hasnt got an official libmtp package. So is there like an unofficial amarok .deb that does has mtp support?

---

### Post by robgue on 2006-10-08
I'm also looking for something like this. haven't found it yet. is there an easy way or instructions on how to compile this?

---

### Post by NESFreak on 2006-10-08
just hope it is included in edgy. Anyone knows? i found out that libmtp IS included in edgy tru package online package search. Anyone tried it out?/ is willing to check if you van select mtp from the amarok adding a mediadevice menu? As long as edgy isn't 2 month delayed i think i can wait until then.

NESFreak

---

### Post by shakespeare on 2006-10-12
AFAIK, libmtp and libnjb are needed, with newer versions than those in the Ubuntu repositories. You could try the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=135845&highlight=mtp"). This works with gnomad2, provided you get gnomad2 source code from sourceforge and recompile with the updated libraries. I have not tried amarok (or other KDE stuff); perhaps it has additional requirements.

- John.

---

### Post by NESFreak on 2006-10-30
GG just checked out mtp in edgy. libmtp is in the repros ([http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmtp)](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmtp)), but both amarok and gnomad2 aren't compiled with it. It's gpl'ed why isn't it just included by default!!!???!! So i just hope I CAN compile in edgy, cause something screwed it up for me in dapper.

NESFreak.

---

### Post by robgue on 2006-10-31
i got it working in edgy. i followed this for edgy after a clean install. all credit goes here. [http://evolvedlight.co.uk/?p=13](http://evolvedlight.co.uk/?p=13)

HOWTO: Install MTP support for Amarok in Ubuntu

A little explanation:

    * Amarok is one of the best media players for Linux/Ubuntu
    * Amarok, in Ubuntu, comes without MTP support
    * MTP is short for “Music Transfer Protocol”. Its not very widely used, sucks quite a lot, and is used in the latest Creative firmwares.

So, we need to get a copy of Amarok with MTP support.

You could compile it with MTP support, but you need libusb, and libmtp which are sometimes hard to come by.

So, we need to do the following steps: (in gnome-terminal)
wget [http://www.imbrandon.com/packages/887D9FD2.gpg](http://www.imbrandon.com/packages/887D9FD2.gpg)

sudo apt-key add 887D9FD2.gpg

sudo gedit /etc/apt/sources.list

Add the following lines:

deb [http://imbrandon.com/packages](http://imbrandon.com/packages) dapper amarok

deb-src [http://imbrandon.com/packages](http://imbrandon.com/packages) dapper amarok

(Replace dapper by edgy if you are using edgy as I am)

Then go sudo apt-get install amarok, or just use update manager to update amarok

Enjoy!






I'd had been trying to get amarok working with my zen vision m for the longest. It finally works! for some unknown reason i have to run it with the command : sudo amarokappp

i dunno why of course.

---

### Post by naholyr on 2006-11-22
It just don't work at all, if it worked once. The package in this deposit, as in the official one, does NOT include MTP support. Just try  "locate mediadevice | grep mtp", i don't think you have one unless you compile Amarok from sources :(

---

### Post by NESFreak on 2006-11-22
uhm don't know that much bout developing but i think this amarok libmtp support thing is plugin based looking at how my amarok supports the other protocols: ```
locate mediadevice
``` gives```

/usr/share/services/amarok_generic-mediadevice.desktop
/usr/share/services/amarok_ifp-mediadevice.desktop
/usr/share/services/amarok_ipod-mediadevice.desktop
/usr/share/services/amarok_njb-mediadevice.desktop
/usr/share/services/amarok_daap-mediadevice.desktop
/usr/lib/kde3/libamarok_generic-mediadevice.la
/usr/lib/kde3/libamarok_generic-mediadevice.so
/usr/lib/kde3/libamarok_ifp-mediadevice.la
/usr/lib/kde3/libamarok_ifp-mediadevice.so
/usr/lib/kde3/libamarok_ipod-mediadevice.la
/usr/lib/kde3/libamarok_ipod-mediadevice.so
/usr/lib/kde3/libamarok_njb-mediadevice.la
/usr/lib/kde3/libamarok_njb-mediadevice.so
/usr/lib/kde3/libamarok_daap-mediadevice.la
/usr/lib/kde3/libamarok_daap-mediadevice.so
```

so i guess the only thing you should do is install
/usr/lib/kde3/libamarok_mtp-mediadevice.so
/usr/lib/kde3/libamarok_mtp-mediadevice.la
/usr/share/services/amarok_mtp-mediadevice.desktop

Any anyone willing to supply me these files so i can try out?

NESFreak

---

### Post by steiftier on 2006-11-28
Hi,
I've the same player. I also can't mount it and I do get following error during mtp-detect

LIBMTP_Get_File_To_File_Descriptor(): Could not get file from device (296)
PTP: Closing session
inep: usb_get_endpoint_status(): Broken pipe
outep: usb_get_endpoint_status(): Broken pipe
OK.

I'm using libusb-0.1.12, and libmtp-0.0.21 . Has anyone tried mtp-format ? I'm thinking about it, cause even MP10 and MP11 have not been able to play all of my music files. The funny thing was that the files mus be OK cause all are played but some only with firmware 1.3 other with firmware 2.1 and some by both firmwares.

---

### Post by steiftier on 2006-11-28
during format i got this error :(

```
IBMTP_Format_Storage(): failed to format storage
Return code: 0x02ff (look this up in ptp.h for an explanation).
PTP: Closing session
inep: usb_get_endpoint_status(): Broken pipe
outep: usb_get_endpoint_status(): Broken pipe
Failed to format device.

```

---

### Post by roger99 on 2006-12-04
> **robgue said:**
> i followed this for edgy after a clean install. all credit goes here. [http://evolvedlight.co.uk/?p=13](http://evolvedlight.co.uk/?p=13)

HOWTO: Install MTP support for Amarok in Ubuntu

I also followed this guide using his repos and debs with MTP support compiled into amarok.

I have installed libmtp2.0.0.18-0 through synaptic (the only one that came up when I searched for libmtp in Synaptic) and when I enter mtp-detect it correctly picks up on my Creative Zen Touch. 

But when I loaded the new version of Amarok and try to setup my device it doesn't give me an option of an MTP plugin.  Just the same plugins that were there before.

Any ideas anyone?

---

### Post by imopen on 2007-01-14
I found this post only today and yesterday i did all by myself ](*,) :mrgreen: 

So, i post to help someone who'll buy a MTP device, such as Creative Zen Vision as mine.

I recompile all amarok and let on /usr/local/ directory... then i found the differences, and i have seen there was only 3 files with MTP... i copied them on /usr/lib/kde3/ and /usr/share/services... and now amarok have MTP support and see my mp3 player 8) 

It's exact what post NESFreak:

> **NESFreak said:**
> 
so i guess the only thing you should do is install
/usr/lib/kde3/libamarok_mtp-mediadevice.so
/usr/lib/kde3/libamarok_mtp-mediadevice.la
/usr/share/services/amarok_mtp-mediadevice.desktop

Any anyone willing to supply me these files so i can try out?

NESFreak

;) 

I don't know if is legal, i could post in attach the three files, if someone needs them ;) 

Let me know if someone needs. ;) 

Bye :)

---

### Post by buddyx6 on 2007-01-14
I would love those files. I can't seem to get them anyway I try.

If I'm understanding you I just place the files in the directory and the MTP plugin for devices will start appearing in Amarok?

---

### Post by NESFreak on 2007-01-15
> **imopen said:**
> I found this post only today and yesterday i did all by myself ](*,) :mrgreen: 

So, i post to help someone who'll buy a MTP device, such as Creative Zen Vision as mine.

I recompile all amarok and let on /usr/local/ directory... then i found the differences, and i have seen there was only 3 files with MTP... i copied them on /usr/lib/kde3/ and /usr/share/services... and now amarok have MTP support and see my mp3 player 8) 

It's exact what post NESFreak:



;) 

I don't know if is legal, i could post in attach the three files, if someone needs them ;) 

Let me know if someone needs. ;) 

Bye :)

It was just a guess. Sometimes I'm stunned by my own logic. Glad it works.

so well uhm. PLZ PLZ gimme teh filez m8. You can post them cause it's GPLed. Thanks.

NESFreak

---

### Post by imopen on 2007-01-18
sorry for late answer, ok this night i'll post the files (i'm at work now) ;)

---

### Post by imopen on 2007-01-18
> **buddyx6 said:**
> I would love those files. I can't seem to get them anyway I try.

If I'm understanding you I just place the files in the directory and the MTP plugin for devices will start appearing in Amarok?

yes, it's so :) 

tonight i'll post the files ;)

---

### Post by imopen on 2007-01-18
In attachment the files, copy them on the right directories and let me know if amarok is able to see MTP device, it should ;)

p.s. the files are for amarok 1.4.4

---

### Post by joshlfisher on 2007-01-18
I just copied them to the correct directories, and restarted amarok. When I plugged in my samsung yp-t7j, nothing happened.  I can configure it manually, and it can connect, but when I try to transfer files, Amarok Freezes.

---

### Post by imopen on 2007-01-18
i'm sorry i don't know your player :-k 


have you tried with libmtp-dev command-line commands? 

/usr/bin/mtp-delfile
/usr/bin/mtp-detect
/usr/bin/mtp-files
/usr/bin/mtp-folders
/usr/bin/mtp-getfile
/usr/bin/mtp-getplaylist
/usr/bin/mtp-hotplug
/usr/bin/mtp-newfolder
/usr/bin/mtp-playlists
/usr/bin/mtp-sendfile
/usr/bin/mtp-sendtr
/usr/bin/mtp-tracks
/usr/bin/mtp-trexist

try one of these ;)

---

### Post by joshlfisher on 2007-01-18
This is most interesting. I tried playing around with the MTP- commands, and came up with something. (I think)

> mtp-hotplug
# This usermap will call the script "libmtp.sh" whenever a known MTP device is attached.

# Creative Zen Vision
libmtp.sh    0x0003  0x041e  0x411f  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Portable Media Center
libmtp.sh    0x0003  0x041e  0x4123  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Xtra (MTP mode)
libmtp.sh    0x0003  0x041e  0x4128  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Second generation Dell DJ
libmtp.sh    0x0003  0x041e  0x412f  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Micro (MTP mode)
libmtp.sh    0x0003  0x041e  0x4130  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Touch (MTP mode)
libmtp.sh    0x0003  0x041e  0x4131  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Dell Pocket DJ (MTP mode)
libmtp.sh    0x0003  0x041e  0x4132  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Sleek (MTP mode)
libmtp.sh    0x0003  0x041e  0x4137  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen MicroPhoto
libmtp.sh    0x0003  0x041e  0x413c  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Sleek Photo
libmtp.sh    0x0003  0x041e  0x413d  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Creative Zen Vision:M
libmtp.sh    0x0003  0x041e  0x413e  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YH-820
libmtp.sh    0x0003  0x04e8  0x502e  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YH-925
libmtp.sh    0x0003  0x04e8  0x502f  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YP-T7J
libmtp.sh    0x0003  0x04e8  0x5047  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YP-U2J (YP-U2JXB/XAA)
libmtp.sh    0x0003  0x04e8  0x5054  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YP-F2J
libmtp.sh    0x0003  0x04e8  0x5057  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Samsung YH-999 Portable Media Center
libmtp.sh    0x0003  0x04e8  0x5a0f  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Intel Bandon Portable Media Center
libmtp.sh    0x0003  0x045e  0x00c9  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# JVC Alneo XA-HD500
libmtp.sh    0x0003  0x04f1  0x6105  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Philipps HDD6320
libmtp.sh    0x0003  0x0471  0x01eb  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Philipps HDD6320 2
libmtp.sh    0x0003  0x0471  0x014b  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Philipps HDD1630/17
libmtp.sh    0x0003  0x0471  0x014c  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# SanDisk Sansa m240
libmtp.sh    0x0003  0x0781  0x7400  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# SanDisk Sansa c150
libmtp.sh    0x0003  0x0781  0x7410  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# SanDisk Sansa e200
libmtp.sh    0x0003  0x0781  0x7420  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# SanDisk Sansa e260
libmtp.sh    0x0003  0x0781  0x7420  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver Portable Media Center
libmtp.sh    0x0003  0x1006  0x4002  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver Portable Media Center
libmtp.sh    0x0003  0x1006  0x4003  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T10
libmtp.sh    0x0003  0x4102  0x1113  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T20 FM
libmtp.sh    0x0003  0x4102  0x1114  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver U10
libmtp.sh    0x0003  0x4102  0x1116  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T10
libmtp.sh    0x0003  0x4102  0x1117  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T20
libmtp.sh    0x0003  0x4102  0x1118  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T30
libmtp.sh    0x0003  0x4102  0x1119  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver T10 2GB
libmtp.sh    0x0003  0x4102  0x1120  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver Clix
libmtp.sh    0x0003  0x4102  0x112a  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver H10 20GB
libmtp.sh    0x0003  0x4102  0x2101  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# iRiver H10
libmtp.sh    0x0003  0x4102  0x2102  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Dell DJ Itty
libmtp.sh    0x0003  0x413c  0x4500  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Toshiba Gigabeat MEGF-40
libmtp.sh    0x0003  0x0930  0x0009  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Toshiba Gigabeat
libmtp.sh    0x0003  0x0930  0x000c  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000
# Archos 104 (MTP mode)
libmtp.sh    0x0003  0x0e79  0x120a  0x0000  0x0000  0x00    0x00    0x00    0x00    0x00    0x00    0x00000000

Notice the 14th entry: > # Samsung YP-T7J

Is the libmtp.sh script being called? How can I tell? What does it do?
Is there any documentation on these commands? There was no man entry that I could find. (man mtp-sendfile)

---

### Post by imopen on 2007-01-19
Call mtp-detect and look if you are able to see your player. 

With mtp-folders you are able to see all directory listing of your player.

Then calling mtp-sendfile without parameters you can see which parameters are expected. ;) 

usage: sendfile [ -D debuglvl ] [ -q ] -t type <path> -f "Folder Name"


mtp-sendfile -t avi -f "Video" hello.avi

;)

---

### Post by NESFreak on 2007-01-19
> **imopen said:**
> In attachment the files, copy them on the right directories and let me know if amarok is able to see MTP device, it should ;)

p.s. the files are for amarok 1.4.4

ahh man you rock. Works perfect for me.

thanks,
NESFreak.

---

### Post by NESFreak on 2007-01-19
> **joshlfisher said:**
> This is most interesting. I tried playing around with the MTP- commands, and came up with something. (I think)


Notice the 14th entry: 

Is the libmtp.sh script being called? How can I tell? What does it do?
Is there any documentation on these commands? There was no man entry that I could find. (man mtp-sendfile)

DOES it works for you in GNOMAD2?
NESFreak

---

### Post by buddyx6 on 2007-01-19
Thank you for the files. I put them in the directories and got the choice for MTP device in Amarok. However Amarok still can't connect. When I run mtp-detect my MP3 player isn't detected.  I have a Siren Edge 4GB player.  I noticed that its not listed when I run the mtp-hotplug. Is there a way to add it to the list?

Thanks for your help.

---

### Post by NESFreak on 2007-01-20
> **buddyx6 said:**
> Thank you for the files. I put them in the directories and got the choice for MTP device in Amarok. However Amarok still can't connect. When I run mtp-detect my MP3 player isn't detected.  I have a Siren Edge 4GB player.  I noticed that its not listed when I run the mtp-hotplug. Is there a way to add it to the list?

Thanks for your help.

can you plug in the device and post the output of the command "lsusb" from the terminal?

NESFreak

---

### Post by NESFreak on 2007-01-20
> **NESFreak said:**
> can you plug in the device and post the output of the command "lsusb" from the terminal?

NESFreak

guess i can make a somewhat more generic explanation on how to get your "random not supported mtp-device" working.

first of all install libmtp-dev (if it isn't already installed).
then go to the commandline and enter "lsusb" while your device is pluged in and activated.
for me it looks like.```
:~$ lsusb
Bus 003 Device 006: ID 041e:413d Creative Technology, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 0000:0000 
```
you can see my zen sleek photo is identified as "041e:413d Creative Technology, Ltd"
the device id is very important. for me it is 041e:413d which i should remember.
now from the command line you should run the command "sudo gedit /etc/udev/rules.d/65-libmtp.rules".
Go to the very end of the document and enter just above "LABEL="libmtp_rules_end""```
# {whatever you wanna name your random not supported mtp-device}
SYSFS{idVendor}=="{the first part of the device id, for me it was 041e}", SYSFS{idProduct}=="{the second part of the device id, for me it was 413d}", SYMLINK+="libmtp-%k", MODE="666"
```
so for me it would look like```
# Creative Zen Sleek Photo
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413d", SYMLINK+="libmtp-%k", MODE="666"
``` save the file.
now restart udev by entering "sudo /etc/init.d/udev restart" on the commandline.

Now all should work.

NESFreak

---

### Post by trippinnik on 2007-02-24
I am having a problem where mtp can't detect my device.  It's a Gigabeat p20.  I have the latest libmtp that I comiled from source forge, I have also tried the one in the repos, but it doesn't detect my device.  Any ideas?

---

### Post by bg1256 on 2007-02-24
I have a Samsung YP-T7J as well, and I've read everything and still had no luck with Amarok.

Some of this is still over my head, and if a solution was found, I am not sure how to find it.  I followed the directions on the first page and compiled the zip file.

What else do I need to do?

---

### Post by bg1256 on 2007-02-24
Well, when I start Amarok, I now get the following message:

```
KLibLoader could not load the plugin:
libamarok_mtp-mediadevice
Error message:
/usr/lib/kde3/libamarok_mtp-mediadevice.so: undefined symbol: _ZN6Amarok9StatusBar10s_instanceE
```

---

### Post by trippinnik on 2007-02-25
Thanks! That was perfect I was hoping I could just add the USB ID to some file I just didn't know what file.

---

### Post by trippinnik on 2007-02-25
That was premature:
I get this from mta-detect
Autodetected device with VID=0930 and PID=000f is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
Connected to MTP device.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP_Get_Storage(): Could not get storage info
LIBMTP_Get_First_Device(): Get Storage information failedLIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
No tracks.
PTP: Closing session
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.

and now amarok crashes when I try to connect to it.  But at least the thing charges now.  Any ideas?

---

### Post by NESFreak on 2007-02-26
> **trippinnik said:**
> That was premature:
I get this from mta-detect
Autodetected device with VID=0930 and PID=000f is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
Connected to MTP device.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP_Get_Storage(): Could not get storage info
LIBMTP_Get_First_Device(): Get Storage information failedLIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
No tracks.
PTP: Closing session
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.

and now amarok crashes when I try to connect to it.  But at least the thing charges now.  Any ideas?

well, it should work, maybe you should try to contact the development team.
NESFreak

---

### Post by NESFreak on 2007-02-26
> **trippinnik said:**
> That was premature:
I get this from mta-detect
Autodetected device with VID=0930 and PID=000f is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
Connected to MTP device.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP_Get_Storage(): Could not get storage info
LIBMTP_Get_First_Device(): Get Storage information failedLIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
LIBMTP panic: Found a bad handle, trying to ignore it.
No tracks.
PTP: Closing session
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.

and now amarok crashes when I try to connect to it.  But at least the thing charges now.  Any ideas?

Well it should work. Or it must be some compatebility problem with amarok itself.

---

### Post by suicideducky on 2007-02-28
ok just found this thread. i use ubuntu but am actually trying to get this working in gentoo.
the only problem is that i have amarok 1.4.5 not 1.4.4 so the files dont work for me :( (tried them with no success) ive tried about 90% if the things in here. i have a samsung YP-K5 it can be detected with mtp-detect. i can see the tracks by mtp-tracks and i can see the folders by mtp-folders.

but how do i access it with amarok? i can see its there, how come the files wont work for the new amarok?

---

### Post by 8solo5 on 2007-03-06
for me

```
giulio@giulio-laptop:~$ mtp-detect
Autodetected device "Philipps HDD6320 2" (VID=0471,PID=014b) is known.
usb_claim_interface(): No such file or directory
Connection error.
No devices.
giulio@giulio-laptop:~$ mtp-folders
Autodetected device "Philipps HDD6320 2" (VID=0471,PID=014b) is known.
usb_claim_interface(): No such file or directory
Connection error.
No devices.

```

---

### Post by bg1256 on 2007-03-06
I'm not sure if this thread is still being supported, but I get an error message every time I start Amarok after unzipping the attached files.

How can I remove them?

edit:

Here is the error message I'm getting, and I'm using amarok from the repo's.

> KLibLoader could not load the plugin:
libamarok_mtp-mediadevice
Error message:
/usr/lib/kde3/libamarok_mtp-mediadevice.so: undefined symbol: _ZN6Amarok9StatusBar10s_instanceE

---

### Post by NESFreak on 2007-03-11
> **bg1256 said:**
> I'm not sure if this thread is still being supported, but I get an error message every time I start Amarok after unzipping the attached files.

How can I remove them?

edit:

Here is the error message I'm getting, and I'm using amarok from the repo's.

since it's just a zip file and while unzipping it didn't overwrite anything, the only thing you should do is removing the files from your hard disk.

/usr/lib/kde3/libamarok_mtp-mediadevice.so
/usr/lib/kde3/libamarok_mtp-mediadevice.la
/usr/share/services/amarok_mtp-mediadevice.desktop

NESFreak.

btw has someone compiled amarok? so the files could be posted her again for version 1.4.5?

---

### Post by skralljt on 2008-02-01
I was having this problem with mtp and then found out I could just let my gigabeat automount and in amarok select generic audio device.  It shows up in amarok just great.  Forget mtp!

---

### Post by NESFreak on 2008-02-10
> **skralljt said:**
> I was having this problem with mtp and then found out I could just let my gigabeat automount and in amarok select generic audio device.  It shows up in amarok just great.  Forget mtp!

it's now supported by ubuntu by default. This thread dates back from the time that that wasn't the case. Everything should now work out of the box.

---

