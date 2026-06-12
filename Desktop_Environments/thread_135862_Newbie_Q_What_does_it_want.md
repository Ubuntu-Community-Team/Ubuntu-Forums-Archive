---
title: "Newbie Q? What does it want?"
date: 2006-02-24
forum: Desktop Environments
---

### Post by DeadTree on 2006-02-24
I'm an extreme newbie. I got my disks, installed, went smoothly, I think, it said to remove cd, sure, reboot, no problem, username, ok, password, ok, it says something about free software and gives me a (place?) I think to find it /user/share/doc/*/copyright and a blinking command line ~$

What does it want? What do I type? Do I put the disk back in?

I typed the /user/share/doc/*/copyright didn't work
I typed 'help', I got something, a bunch of something on the screen...wasn't too helpful.

I'm normally a mac os 9 user and haven't used a command line since appleIIe I think. 

This is a Asus brand pentium III pc, 650mhz with a samtron monitor, and a hp  serial mouse and keyboard.

Btw, I changed it to boot from cd before install did the install change this setting to boot from the hd automatically or do i need to change that?

Any help and handholding appreciated, dt

I can't get the smilies to work, they don't appear where my cursor is but elsewhere in my message...what up with that?

---

### Post by lamego on 2006-02-24
Hum, are you sure you didn't selected the "server" option on the install ?
You should get a graphical interface or at least an error telling it was unable to start X .
After loging in try the command: 
```
 startx
```
That should start the window manager (I guess that's what you are looking for).
If X doesn't start, try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DeadTree on 2006-02-24
I suppose i could of installed the server, I remember I did type the word server once but i thought that was what it was telling me to put in...should I reinstall?

dt

---

### Post by lamego on 2006-02-24
If you did install the "server" which is an option, your system is ok. If you want the "desktop" applications next time just hit "enter" for the default desktop install.
Anyway you can install the rest of the desktop now with the command:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by DeadTree on 2006-02-24
I'm getting font config. errors

Can not load default font config file

whats wrong? It keeps installing but it keeps say this.

---

### Post by DeadTree on 2006-02-24
ok:confused:  it installed and seems to be working but it still had those default config font errors throughout the install. Was this suppose to happen? Will this bite me on the butt later?
dt

What the heck is up with those smilies that confused smily was suppose to be at the end of the post?

---

### Post by xmastree on 2006-02-24
If I were you, I'd reinstall. Just hit enter at the prompt and go with the defaults.

> Btw, I changed it to boot from cd before install did the install change this setting to boot from the hd automatically or do i need to change that?No, the install will not change the boot sequence. You are instructed to remove the CD during the install, when it reboots. So long as the second boot device is the hard disk, you'll be fine.

---

### Post by LateNighter on 2006-02-24
I agree REINSTALL using the default Option.

 But when you do just make Sure to let it Format your Drive or the partition it's going on.

 By default Ubuntu won't allow you to Install over an existing Linux/Unix OS.

 Also not to Confuse you any further but you do have an Option of downloading the KDE Desktop through Synaptic once you get Genome installed.

 Since you said you used Apple Mac before theres an option there to have you Desktop look and act like Apple Mac.

 I use Windoze for Gaming but nothing else. 
 Other then that it's Ubuntu ALL the WAY.  Theres an Option to that allows me to run it in a Windoze form, but I run it in KDE because when I'm running Ubuntu I don't want to even be reminded of Windoze and the land of Shattering Glass.[-(

---

### Post by cotcot on 2006-02-25
I also agree with reinstall. There is a lot of documentation for ubuntu. You may have a read of some of it to become more confortable before reinstall.  For instance : [https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC) or [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) (contain screen shots, is for dual boot but single boot is almost the same way).

---

### Post by DeadTree on 2006-02-25
Thanks for everyones help. I did reinstall and did the normal version this time. Works fine. I've changed the screen saver cause the first time that test pattern with the thing with the flame came on I thought I toasted something bad or something...should be a warning on that thing..."Don't panic this is just your screen saver" :)   I can't believe there is an appleII screen saver...

It not on a dual booting machine, its on this pc I got with no os from the local thrift for a whopping $15.99. The dang thing has not only its original 13 gig hd but a second 80 gig one too. It also has a fancy video card and a scsi port. It musta been someone's pride and joy when it was new, not a spec of dust in the interior.

Some questions, does ubuntu support scsi and if yes do I need to find a driver, if yes where should I look for drivers? 

Second, while installing it told me there was no selected network connection card, but there is an ethernet port on the back, did it not see this or isn't that what it was talking about? does it need drivers? Where do I get them? 

Can i network my macs to this computer? If yes I might need help later cause I ain't ready for that. 

I'm not getting any sounds from the speakers, does this mean the sound card needs drivers too?

Thanks dt

---

### Post by John Jason Jordan on 2006-02-25
[QUOTE=DeadTree]Some questions, does ubuntu support scsi and if yes do I need to find a driver, if yes where should I look for drivers? [/QUOTE]
Yes, Linux certainly does support SCSI, big time. Linux is very strong in the enterprise world where SCSI rules. In fact, I'm surprised your installation did not auto-detect the SCSI card. To find what card you have to into System > Administration > Device Manager. Poke around and see if it's listed there. It may be already installed and working.

One thing that may have happened is that the SCSI card and the disk connected to it were detected, but the installation utility did not format the disk to use for Linux. 

[QUOTE=DeadTree]Second, while installing it told me there was no selected network connection card, but there is an ethernet port on the back, did it not see this or isn't that what it was talking about? does it need drivers? Where do I get them? [/QUOTE]
Ditto the instructions for the SCSI issue.

[QUOTE=DeadTree]Can i network my macs to this computer? If yes I might need help later cause I ain't ready for that. [/QUOTE]
You certainly can. Once your network is running the Linux computer should see the Mac computer over the ethernet. I'm not sure exactly how to get it to talk to the Mac and vice-versa. If it were a Windows computer I know it uses Samba for the interface. I'm sure there is one for the Mac as well. I just don't know what it is.

[QUOTE=DeadTree]I'm not getting any sounds from the speakers, does this mean the sound card needs drivers too?[/QUOTE]
Ditto the instructions for SCSI.

Some of these things may need drivers, some may already have the drivers installed but just need to be configured -- e.g., maybe you're not getting sound because the speakers are turned off or the volume is too low. Start with Device Manager to see what's going on and get the make and model of the card/device. 

Holler back for more help as you stumble along and figure things out. :)

---

### Post by xmastree on 2006-02-25
[QUOTE=DeadTree]that test pattern with the thing with the flame came on[/QUOTE]That's just a built-in image. If you like open the screensaver, and go to the advanced tab and select 'Grab Desktop Images' that flame thing will be relaced with whatever is on your desktop at the time.

Try it.

---

