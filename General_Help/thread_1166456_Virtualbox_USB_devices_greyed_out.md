---
title: "Virtualbox USB devices greyed out"
date: 2009-05-21
forum: General Help
---

### Post by Stolea on 2009-05-21
I just installed Virtualbox 2.2.2 without any hitches. For some reason my USB devices are listed, but greyed out. Any idea what I have to do do activate them?

---

### Post by gpstar on 2009-05-21
add this to the bottom of /etc/fstab

```

none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

```

replace the devgid number with your devgid number. 

To find that, do

```
grep vboxusers /etc/group
```

and you'll see something like

```
vboxusers:x:125:username
```

where the 125 is the devgid #.

Then after rebooting, usb devices should work.

---

### Post by Stolea on 2009-05-22
I did all that, but the box is still greyed out.
When I run > grep vboxusers /etc/group
I get > vboxusers:x:124:
with no username.
What am I doing wrong?

---

### Post by albinootje on 2009-05-22
> **Stolea said:**
> 
What am I doing wrong?

Put yourself in the vboxusers group. 
Let's assume your username is steveb :
```

sudo adduser steveb vboxusers

```
After that, log out of the GUI, and then log back in, check the groups again with :
```

groups

```

---

### Post by Stolea on 2009-05-22
Printer (and UPS and mouse) still greyed out.
> groups returns
> peter@shop:~$ groups
peter adm dialout cdrom plugdev lpadmin admin sambashare


---

### Post by albinootje on 2009-05-23
> **Stolea said:**
> 
peter@shop:~$ groups
peter adm dialout cdrom plugdev lpadmin admin sambashare

Your username is still not in the vboxusers group, or perhaps you didn't log out ?

Try this (sudo will ask for your own password) :
```

sudo adduser peter vboxusers

```
Then reboot, and try "groups" again.

---

### Post by albinootje on 2009-05-23
And can you post the output of :
```

grep -i vboxusers /etc/group

```

---

### Post by Stolea on 2009-05-24
I wasn't logged out. I now seem to be OK.
Many thanks.

---

### Post by xavierp94 on 2009-05-25
> **Stolea said:**
> I wasn't logged out. I now seem to be OK.
Many thanks.
This happened to me too. A simple solution for me was to go to System>Administration>Users and Groups then unlock the application. After that, select your account and hit properties then to user privileges. Then check use Virtualbox. Log out and log in.

---

### Post by lamachine on 2009-08-28
[LEFT]Hi Guys.  [/LEFT]
 [LEFT]I did have the same problem and overriding fstab as has mentioned gpstar didn’t work.  [/LEFT]
 [LEFT]The solution was adding user privileges as described by xavierp94 in the note May 25th, 2009 . 

Thx
 [/LEFT]
 [LEFT]

[/LEFT]

---

### Post by quakk on 2010-01-22
this did it.  the virtualbox manual just says to make sure all users have read and write access to the group usbfs.  no comments on what that means or how to do it.

thanks!

> **gpstar said:**
> add this to the bottom of /etc/fstab

```

none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

```replace the devgid number with your devgid number. 

To find that, do

```
grep vboxusers /etc/group
```and you'll see something like

```
vboxusers:x:125:username
```where the 125 is the devgid #.

Then after rebooting, usb devices should work.

---

### Post by rosegarden78 on 2010-05-16
I can confirm gksudo gedit /etc/fstab works.  In Lucid this line was missing:
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

I got the devgid from the Users and Groups under Administration.  Just click Manage Groups, look for vboxusers, and make sure your username is checked.  Then reboot.

---

### Post by pentium_pro on 2010-06-22
If my memory serves me well, I think that in previous versions of Virtualbox setup in Ubuntu all was done automatic. I didn't have to manually add myself in vboxuser group like I need in Arch Linux, setup done that automatically.
This time I downloaded .deb package, not apt-get install method. But again, maybe something happened with installation when Oracle took Sun. :D

There is no need to mess with fstab, in my case, I need only:
```
sudo adduser USERNAME vboxusers
```
And log out/in.

---

### Post by juliobahar on 2010-06-23
Wonderful solution, for my lucid lynx and virualbox desktop, I just had to include my name in the vboxusers group. Log out and in and the USB issue was fixed. 

Thanks

---

### Post by bertbuckie on 2010-09-14
cheers pentium pro...... worked a treat :) iphone ( bricked I fear ) is now detected in DFU mode and trying to restore :) --- shame theres no firmware flashing progs for linux I have found ( but then im a linux n00b of sorts..... still tho, got the wife and parents running ubuntu now :D

---

### Post by science.copperfield on 2010-11-08
[FONT=Times New Roman]Are we having fun yet? Yes, I think so. Let me share with you my fun. Some simple specs...[/FONT]

[FONT=Times New Roman]HP 8540P Executive Laptop[/FONT]
[FONT=Times New Roman]4GB RAM[/FONT]
[FONT=Times New Roman]320 GB HD[/FONT]
[FONT=Times New Roman]1GB Nvidia [/FONT]
[FONT=Times New Roman]Intel Core i7 Processor[/FONT]
 
...it's about two weeks old.
 
Ubuntu 10.04 LTS (the image is a couple of months old)
 
Attached is an external USB 750GB IDE Hard Drive. That's where I'm pointing all my VDIs to. 
 
Today I spent getting VirtualBox updated to version 3.2.1.0 r66523
Installed VirtualBox Guest Editions (same version number)
Installed XP_SP3_32 Bit
Installed MS Office 2010
Installed Cisco VPN Client (ipsec version)
Installed ActivClient 6.2
 
Card Reader is an SCR3310
 
So...everything works great... I'm writing this message from the virtual xp, which has its vdi on a usb hard drive, I'm using my usb mouse, and all seems right with the world...except the SCR3310. Like my friends above, the usb devices are all greyed out.
 
So first, I tried to add the line:
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0
...to the bottom of my fstab.
 
Then I shut down windows, exited the virtualbox, and rebooted my entire system....but it didn't come back! It spit and coughed....gave me the finger, and said something about not mounting my usb devices. My choices were to press S to skip or M for manual. I chose M which droped me to a command line console screen. So I vi'ed the fstab file and put a # in front of my recent addition, then rebooted again.
 
And wouldn't you know it...pixies started dancing and my system started up again normally.
 
Next I read onwards, and someone said that messing with the fstab had nothing to do with why it wouldn't boot. It's that I'm not in the right group. Ah yes....simple universal unix...doh! Once again, I closed out of my virtualbox session, and did the useradd thing, then tried to just log out and log back in again. 
 
Well my system liked that even less, and began hurling rotten packets at me. It wouldnt' actually log out. I sat there for about 20 minutes looking at the "I'm thinking about it" dots...finally I did what you should never do to a unix-ish file system and crashed it...held down the power button and prayed for mercy.
 
I powered the system back up, and it actually came back nicely. So I launched the trusty virtualbox, and it looked like everything was going well, but I lost my usb mouse and could only use my touch pad and trackball. Then my USB Hard drive went away, and my virtualbox image gave me a ntoskrnl not found error. That's windows speak for "go away, I hate you." When I exited virtualbox, all my usb devices came back.
 
So I undid my doings and took my username out of the virtualbox group again, and here I sit...perplexed, frustrated, and trying NOT to visualize what it was like when the cops showed up to free the porn star from the closet of Charlie Sheen's hotel room.
 
I'm going to watch a movie. :popcorn: You guys let me know when you've got this figured out :P

---

### Post by science.copperfield on 2010-11-10
and...drum roll please..... I got it working.

What happened? I have no friggin clue.

Yesterday I did "sudo adduser USERNAME vboxusers" and it went all LAPD on me.

Today, in the filters, I turned all everything except the mouse and the smart card reader, then did "sudo usermod -aG vboxusers <my username>, rebooted and *cue fanfare music*  It's working!  

You know the old windows haiku
Yesterday it works
Today it doesn't work
Windows is like that.

Well... 
Yesterday it was broke
Today it works
WTF Happened? LOL

---

### Post by 0ziris on 2011-04-12
Had the same problem in Maverick Meerkat. After I added user to the vboxusers logout/login didn't help. So just to be on the safe side I rebooted and voile. All greyed out USB devices are now accessible.

---

