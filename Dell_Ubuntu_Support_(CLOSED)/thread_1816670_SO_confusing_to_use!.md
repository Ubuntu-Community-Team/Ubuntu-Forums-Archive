---
title: "SO confusing to use!"
date: 2011-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Newguyhere on 2011-08-02
Newbie to Ubuntu here. 
On my Dell i6000 (XP Win. Media Ed. 2005)

Apparently my HD needs to be replaced, & I'm trying to get the data off it 1st before doing so. Several suggested Ubuntu to me & so I installed it on a flashdrive.

Seemed to work when I saw my black screen turn into a "Matrix"-looking screen w/ Aaaaal these numbers scrolling up by themselves, until it stopped at a line that read:

"BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of commands."

I downloaded 11.04 desktop -i386.iso version.  This is where I got a bit lost. The instructions told me to find "Ubuntu Desktop Edition".  Ok. I did not see that. So I used the one closest to what I have. (the 11.04 thing)

So I *did* see the Ubuntu screen w. the logo, it did its thing & then the "Matrix" stuff, then the stopped line I mentioned above. 

What now? Thanks for Any hand-held help...

---

### Post by ajgreeny on 2011-08-02
Did you really install it to the flash drive, or are you using it as a live USB at the moment?  If you did install it, how did you do that?

---

### Post by Newguyhere on 2011-08-02
I used another laptop & 1st thing I did was put the 11.04 desktop -i386.iso version on the flashdrive. Then I downloaded & installed the [Universal USB Installer]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe") on the flash'.

Then I put the flash' in *my* laptop & it did its thing from there.

---

### Post by ugm6hr on 2011-08-02
Couple of things:
1. Did you check the md5sum of the iso?
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Windows
2. What instructions did you follow?

If you have created the USB correctly, and it doesn't boot - the simplest thing is to try other Linux OS versions rather than work out what's wrong. If anything, it is likely to be a graphics driver issue - I can't remember if Ubuntu offers a safe mode from the Live USB any more.
Some alternative suggestions: Puppy Linux, AntiX

---

### Post by dcollier on 2011-08-02
Download knoppix to a cd, boot from cd, copy or backup data to an external location.

---

### Post by Newguyhere on 2011-08-02
> **ugm6hr said:**
> Couple of things:
1. Did you check the md5sum of the iso?
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Windows
[B]
Never even *knew* about that or that I needed to do it.[/B]


2. What instructions did you follow?
[B]These. 
[/B][http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[B]
I went to the "Burn Your CD or Create a USB Drive" section, clicked USB Stick/ Windows, & did my best from there.
[/B]

If you have created the USB correctly, and it doesn't boot - the simplest thing is to try other Linux OS versions rather than work out what's wrong. If anything, it is likely to be a graphics driver issue - I can't remember if Ubuntu offers a safe mode from the Live USB any more.
Some alternative suggestions: Puppy Linux, AntiX

I guess I can try the Linux OS thing, if you or someone could walk me through it step-by-step like I'm 6.  =/


dcollier- I'll give that a whirl if all else fails. Thx.

---

### Post by Newguyhere on 2011-08-04
" if you or someone could walk me through it step-by-step like I'm 6."

No takers for *that* job, eh?...

---

### Post by SeijiSensei on 2011-08-04
Boot the CD, then when the main Ubuntu menu appears, hit F6 to bring up a list of options that you can add to the boot process.  Click on the "nomodeset" option; an "X" will appear next to it.  Now hit Escape, then Enter to boot with this option enabled.

---

### Post by Newguyhere on 2011-08-04
Thanks, 'Sensei.

I actually tried it from a flashdrive. I saw a screen similar to this:
[http://news.softpedia.com/images/extra/LINUX/large/ubuntu910alpha6-large_000.jpg](http://news.softpedia.com/images/extra/LINUX/large/ubuntu910alpha6-large_000.jpg)

Then after hitting F12, I saw a screen offering an Installer boot menu:

Run Ubuntu from this USB
Install Ubuntu on a hard disk
Test Memory
Boot from first hard disk
Advanced options
Help

If I hit 'R', it would do all this crazy Matrix-looking mumbo jumbo, then stop & wait for some kind of command. 
Hitting F6 didn't bring me to 'nomodeset'.

---

### Post by walt.smith1960 on 2011-08-04
I don't know if this will help you or not.  If you have a CD drive on the sick machine, a live CD might behave better than a live USB.  I've use Unetbootin to create either live CDs or Live USBs. My desktop won't boot from bootable USB drives but is fine with live CDs.  It is available for either Windows or Linux. Here's the download link:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You just have to keep track of where your .iso file is.  Unetbootin will also offer to find the .iso file itself and make a bootable CD or USB from there. I've not tried that but it should work.  If the Live(whatever) works properly you should have a choice of try or install.  Click on the box/text, not on the 'disk'. Click 'try' and you'll get a functioning OS minus proprietary drivers and updates.  You should see your windows partition and all its folders.

Edit:  Their pages doesn't mention creating a liveCD.  If Unetbootin doesn't do that(it used to and still may), Windows should. Find the downloaded .iso file, right click it in explorer. Is "burn to disk" one of the options?

---

### Post by ugm6hr on 2011-08-05
> **Newguyhere said:**
> Never even *knew* about that or that I needed to do it.

So is the md5sum correct? I assure you you needed to do it.

---

