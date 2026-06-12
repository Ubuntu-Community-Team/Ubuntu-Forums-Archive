---
title: "AARGH! Need assistance with Dell Mini 9.1!"
date: 2010-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mbrett on 2010-03-22
If I can vent for one moment. I really dig the idea of Linux. I do. I loathe Windows, for many different reasons. But let me just say the two months of time I've spent with the used Dell Mini 9 I purchased has been as frustrating as my adolescence.

There. Needed to get that off my chest.

Here's the big issue. As you are aware, some Dell Mini 9s shipped with dink-*** HDs. Each time I reboot my Mini, I quickly fill it up with just apps. I get it. This machine was not meant to game or do anything but crawl the web.

But I bought this machine because everybody raved about how you could soup it up. So this weekend I plunged. I bought the 2GB RAM. I bought the 32GB SD. Perfecto!

Np perfecto.

You see, my Dell Mini only boots from the USB pen drive shipped to me by Dell which automatically installs Ubuntu to the puny HD. Therefore, all updates and apps work directly from there.

I know, grab a Live USB Boot Ubuntu Netbook Remix? Done. Except this shite machine only boots the Dell USB, not the one UNR USB boot I create. Yes, I've downloaded the image more than once. Yes, I turned off all firewalls, anti-virus, and cloaking devices. When I plug the UNR USB Boot into my desktop, it reads it just fine. And I know the Dell Mini can boot from there because the Dell USB does. 


AAAAAAH!!  [Wondering why I'm a liberal arts major, when I could have the world for a computer science degree]

When I boot from USB in bios with the UNR USB Boot, I get this:

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM
j

And then nothing more than the sheer blackness HAL offered that unfortunate astronaut.

Again. And again.

And.

Again.

So anyone who can tell me how to get this 15 X 8 instrument of insanity to run UNR 9.1 from the SD, please let me know.

If you hear anything, it's just me. Banging my head against the wall.

---

### Post by mikewhatever on 2010-03-22
Can you relate how you made the unr usb? Apparenly, not all methods work with all distros, but I've seen other reporting successful installations of non-Dell Ubuntus.

---

### Post by mbrett on 2010-03-22
> **mikewhatever said:**
> Can you relate how you made the unr usb? Apparenly, not all methods work with all distros, but I've seen other reporting successful installations of non-Dell Ubuntus.

I've used unetbootin and Universal USB Installer.

What I would really, really. really love is if there was someone out there with a workable Dell Mini 9 bootable USB. 

Because somehow this Dell ain't reading it.

4GB SSHD. Ugh. Dell doesn't even sell the 8GB upgrade anymore.

Mike

---

### Post by KegHead on 2010-03-22
Hi!

WOW!

This is very unusual.

My mini 9 came with Ubuntu installed and I've upgraded to new versions with no problems via USB.

Specs: 2gb ram, 16 gb ssd hd.

I'm curious to hear about a solution.

KegHead

---

### Post by mbrett on 2010-03-22
Oh, this info may help. When I go to boot bios there is no plus by USB storage. I guess that means that it can only be booted from the HD. Don't know how the Dell USB does it.

Anybody know how I can turn on USB boot?

If anyone would like to ship me a working Live Dell Mini 9 UNR USB, I would compensate them in kind. Just message me.

---

### Post by CharlesA on 2010-03-22
See if it has a hard drive boot order in the BIOS, I had to change a setting in there so that it would boot from usb on a couple of my desktop machines.

---

### Post by OCAristRocker on 2010-03-24
I had the same issue for my dell mini 9 4GB trying to make the usb stick on my macs. My solution required me to use a PC with a cd drive.  Here's what I did:

1) I downloaded Ubuntu Netbook Remix and burned onto CD. 
2) It comes with usb-creator.exe. I ran it and pointed to where the ubuntu image was (on cd) and created a bootable usb drive with ubunutu. 
3) When I turned on my mini, I held down "2" to go the BIOS. Changed the boot order to usb first. 
4) Restarted and install began.

I had so much trouble trying different methods but that seemed to work. For some reason wifi isn't working, but I'll search the forums for a solution. I plug into ethernet good for now.

---

### Post by ugm6hr on 2010-03-24
I would suggest one of the following options:
1. Use the 9.04 NBR - it came as a USB ready file
2. Use unetbootin on a Windows PC - I had similar headaches using it on Ubuntu, only to find that most of the time it wasn't bootable.

Unfortunately, since 9.10, the NBR has been distributed as an ISO.  Which is stupid.  And the official ISO -> USB app isn't available for the Dell Mini version of Ubuntu (which is "lpia" rather than "i386").

PS: This info may be outdated, since I haven't done any of this for several months on my Mini - still running 9.04 til 10.04 is stable.

---

### Post by snowpine on 2010-03-25
> **mbrett said:**
> So anyone who can tell me how to get this 15 X 8 instrument of insanity to run UNR 9.1 from the SD, please let me know.

Now hold on a second... are you trying to boot from a USB flash drive, or from an SD card? The Dell Mini 9 is physically incapable of booting from SD due to the BIOS.

---

### Post by mbrett on 2010-03-26
A little update. I bought a 16gb solid state HD. So now my HD has been replaced. First problem, solved.

Second problem, same as the first.

It turns out to check out some of the Linux games I have to upgrade to at least 8.1. Which Dell won't let me do from their OS.

So I'm back where I began. But...I have an external CD drive coming in the mail any day now.

I want to make this machine dual boot so I can watch mlb games with my subscription. So I need a windows OS on my hd.

I'm going to wait until my cd drive gets here to reboot all this. I will keep you posted.

---

### Post by Talon2 on 2010-03-26
> **OCAristRocker said:**
> 
3) When I turned on my mini, I held down "2" to go the BIOS. Changed the boot order to usb first. 
4) Restarted and install began.


In reading this thread I've noticed that nobody has mentioned that there is another BIOS setting that is required in order for a successful boot to a usb flash drive:

USB BIOS Legacy Support: Enabled

If this setting is wrong you can try to boot from a usb flash drive indefinitely and it won't work.

---

