---
title: "Ubuntu 8.10 on a Dell Inspiron 2600"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marillion2k on 2009-03-22
**:( SIGH :(**

OK. This is beyond frustrating now. Fellow Ubuntu-on-a-dell users, please assist!! I will detail my installation issues below :

I own a very old Inspiron 2600 Dell Laptop : 

* Celeron 1.0 GHz processor
* 256 MB RAM
* 20 GB HD
* Intel 830 Graphics Chipset

It has a few 'defects'. First off, the cd-rom won't boot anymore. I have tried everything from updating the BIOS to chatting with DELL support, and the only conclusion I have is that there is something wrong with the internal cd-rom. It still works regularly though, just won't boot. I also have a wifi PCMCIA card installed (Belkin 802.11G wireless notebook card) and that seems to be an issue ... 

Let me explain the torture I went through trying to get this to install properly. First time, I downloaded the regular version of ubuntu 8.10 and tried the install, when starting the GUI portion of the installer my screen started to display horizontal lines and a garbled what looked to be a wallpaper, but really distorted. So that didn't work. Searched the internet for answers and found that the problem has to do with my chipset (intel 830) does not play nicely with Ubuntu/Debian etc. A lot of people described editing the xorg.conf file in /etc/X11/ with certain values.

At time of install, I still also had windows xp home edition installed. Since my cd-rom won't boot, I started the installer from within Windows and got it to a point where there was a dual boot option (ubuntu/windows). I had no idea how to edit the xorg.conf file. Then I read about an alternate installation disc for ubuntu so I tried it (using the Smart Boot Manager floppy to get it to boot from the CD-ROM). This installed finally. Yet, booting into Ubuntu still showed lines and garble.

Tried booting into recovery mode. This gave me the option to exit to a command line. After a few attempts I finally was able to edit xorg.conf successfully to the values I found could help. This did not help at all. Now the regular boot option gives me a command prompt in a huge font. Tried starting gnome, by entering 'gnome-session', but that errored out with a 'device not found' error.

I want to try going back to an older version of the laptop's BIOS but none of my other machines have floppy drives for the BIOS image, except for the now defunct laptop. I guess I could get the executable zip file from DELL and burn the contents onto a cd-rom and boot that cd-rom using the SMB boot manager, do you think?

I'm at a loss here, don't know what else to do to get Ubuntu to install properly, booting into the GNOME GUI. During install and boot up, it also gave me an error having to do with my wireless card, but I just removed the card and plugged the laptop directly into my router using an ethernet cable.

Help. Is there anybody out there that can help me, give me some tips to get this to working. I'm a Linux newbie so you have to be gentle. I most definitely appreciate any help you can give me.

Thanks!!

---

### Post by DeadlyChicken on 2009-04-02
Sorry but this isnt going to be much help, only to say that I also am having trouble with a belikin WiFi 802 g pcmcia card on an ancient lattitude c600 laptop whose cd rom has died.  The wireless  is just not connecting, and I also seem to have double the network cards listed ( two ehternet and two wifi when only one of each seems active  ? ) 

anyhow I found I had some luck by installing ubuntu on this via PXE network boot form another laptop I have with ubuntu on it.  it was a bit of a muddle but I got it going, ended up installing a command line version and then installing gnome from there, but it ended up being a 7.something version ? then I had to update it a couple of times to get to 8.10 but it worked :p its just the wifi now, although gonna do a bit of digging see if I can diagnose the issue

---

### Post by afrodeity on 2010-05-02
I have just installed lucid on a 2650 Inspiron. My only problems are the keymap which is driving me nuts and it running a bit warm.

---

