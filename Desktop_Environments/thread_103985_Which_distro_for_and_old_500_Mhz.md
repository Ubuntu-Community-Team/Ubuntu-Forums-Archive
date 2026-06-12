---
title: "Which distro for and old 500 Mhz?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by ominolore on 2005-12-15
Ok people, once again I need your help. 
I've got here an old Pentium III 500 Mhz and I need to put a working GNU/Linux OS distro on it.. Of course, unluckily breezy is too hard to handle for it.. I'd need something lighter and faster.. just to browse a little the web, check the e-mail and do some document writing (of course, MsWord compatibility would be great to have)..
My experience with linux is too fresh: are my need satisfiable or maybe linux distros for desktop are a fresh bless as well?
Which distro would you install if you were in my shoes?
Thank you, once again.

_A little more about this PC-rescue mission_
[I]This computer is from an italian, educational team working with people with mental disease. In Italy organizations like that are always fundless and out of sovvention, that's why they can't affort a new computer neither a MsWindows OS, even if I think it would be easier for them to use (unfortunately, as we all know, computer skills tend to be teached one way only...)
That's why I'd be very glad to help them. But with your help, folks.;) [/I]

---

### Post by gilgongo on 2005-12-15
You could try one of the "slim" distros - there's Damn Small Linux, for example:

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

"XMMS (MP3, CD Music, and MPEG), FTP client, Dillo web browser, links web browser, FireFox, spreadsheet, Sylpheed email, spellcheck (US English), a word-processor (FLwriter), three editors (Beaver, Vim, and Nano [Pico clone]), graphics editing and viewing (Xpaint, and xzgv), Xpdf (PDF Viewer), emelFM (file manager), Naim (AIM, ICQ, IRC), VNCviwer, Rdesktop, SSH/SCP server and client, DHCP client, PPP, PPPoE (ADSL), a web server, calculator, generic and GhostScript printer support, NFS, Fluxbox window manager, games, system monitoring apps, a host of command line tools, USB support, and pcmcia support, some wireless support."

---

### Post by abou on 2005-12-15
Distrowatch.com is usually a good place to start.  Otherwise, from what I have read, Damn Small Linux (DSL) or Puppy Linux might be what you are looking for.  The cool thing about DSL is that it is a Debian-based system like Ubuntu.

---

### Post by mcduck on 2005-12-15
In my experience, ubuntu with XFCE works nice on a AMD K6-2 @ 500MHz with 120 MB of ram. Even gnome is usable (but slow) if you disable some animations and stuff with gconfed..

OpenOffice is insanely heavy, so some lighter editor would be a good idea.

But yes, Damn Small is ok if you want something lighter..

---

### Post by kaamos on 2005-12-15
I installed breezy on a lifebook with a 500MHz processor and 128 mb of ram. Gnome was slow, but XFCE was very good and ran at a usable speed.

---

### Post by manicka on 2005-12-15
I'd agree, xfce would be a good solution

---

### Post by anthro398 on 2005-12-15
My exprience jives with the comments of the previous posters.  It isn't so much which distribution you run as it is what window manager, services, and applications you run.  I suspect that Ubuntu 5.10 with an ultra lightweight wm will run about as fast as Peanut, DSL, or the other slim distributions.  It will just take some tweaking.  I've run Suse 9.3 with FVWM on Pentium 2 400MHz machines with a max of 129MB of memory.  OpenOffice is a resource glutton to be sure.

---

### Post by djheadley on 2005-12-15
I'm running Breezy on an Intel Celeron Medicino 433 mhz with 256 mb RAM.  It runs just fine for me.  OpenOffive does take a little bit of time to load but other than that I'm satisfied with it.  Oh yeah, I have a 1 gb swap partition.

djheadley

---

### Post by az on 2005-12-15
[QUOTE=ominolore]Ok people, once again I need your help. 
I've got here an old Pentium III 500 Mhz and I need to put a working GNU/Linux OS distro on it.. Of course, unluckily breezy is too hard to handle for it.. [/QUOTE]

How much ram do you have?  The desktop should load quite quickly with even a 400 MHz pentium.  The only thing that should be that slow is firefox.

You need at least 128 megs of ram for the desktop to not be slow.  I find Ubuntu is quicker than WindowsXP in general.  

It is intersting that Ubuntu has been *gaining* speed in the last few releases.  Dapper will be even faster than breezy and breezy is faster than the other previous releases.  You do not need a very modern computer to run Ubuntu.  Just at least 128 megs of ram.
 

[QUOTE=ominolore]
[I]even if I think it would be easier for them to use (unfortunately, as we all know, computer skills tend to be teached one way only...)
 [/I][/QUOTE]

Gnome is more intuitive than Windows.  People who are not familiar with computers will find it easier to learn than Widnows.

---

### Post by simon_is_learning on 2005-12-15
If you make a "server" ubuntu installation then do an apt-get install xubuntu-desktop

I have done it on a 300 Mhz laptop width 64mb ram. I think that it (under the hardware cirumstances) works fine. Though I didn't install xubuntu desktop. I installed xfce and and applications one by one. 

DSL is worked fast on that computer, but i felt limited when trying to configure it to a workstation. I felt more free in ubuntu + xfce.

---

### Post by silex on 2005-12-15
I'll second simon_is_learning here, doing a "server" install and then installing the xubuntu-desktop worked well for me on an old PII 400mhz with 128mb or ram.  Its a nice way to revive an old machine for light or server usage.

---

### Post by ThomasW on 2005-12-15
Well, I have got an old Pentium III 550 MHz with 492MB of RAM and Ubuntu is absolutely fine. I work with openoffice and have to wait a couple of seconds on startup, but then you can work seamlessly.

256MB of RAM should do as well. Look for some tuning tips (especially change the scheduler by adding elevator=cfg on the boot command line in /boot/grub/menu.lst, dma settings for your CDROMs, changing swap behaviour might help as well, etc.)

I'm absolutely impressed by Ubuntu's performance (I had SuSe linux 9.2 with KDE before but was really disappointed).

---

### Post by curtis on 2005-12-15
I would do what already has been suggested with installing the Ubuntu server install.
Then installing the xubuntu-desktop package through apt-get.

---

### Post by Dr. Nick on 2005-12-15
I am running gnome on a p2 366mhz laptop with 128mb of ram. Especially with dapper and the new gnome 2.13.3 it is very useable :) like has already been stated it seems faster with each new version (unlike windows).

Xfce is also a good choice, I use it occasionally but like some of then gnome panel applets. I would give ubuntu a go on it, especially if you are already familar with it from other systems. As far as I know no distro will install on it and be fully featured and blazing fast out of the box, I was in a similar situation with the 366 so I just stuck with what I knew and liked best which was ubuntu and tweaked it for speed, But with my latest dapper install I didnt touch a thing and am very satisfied.

Open Office is slow on it so I use it sparingly. For a good fast msword compatible application take a look at abiword.

---

### Post by az on 2005-12-16
[QUOTE=curtis]Iinstalling the Ubuntu server install.
Then installing the xubuntu-desktop package through apt-get.[/QUOTE]


I think the only advantage to that is saving disk space.  If you can spare the extra gig of disk space, you get all the useful utilities available to you.  By booting into a different desktop environment like XFCE, they do not consume any more memory of CPU power than if they were not on your drive.  It is what you run that takes up memory, not what is installed.

If, for example,  you need to use the networking application or the automounter, it is available that way.

---

### Post by Hairy_Palms on 2005-12-16
i run breezy with icewm on a p2 333mhz with 64mb ram and its fine,

---

### Post by davidsrsb on 2005-12-16
Some Slackware spinoffs like STX are OK on a P11 and very fast on a P111
The choice of applications is important, go for Abiword instead of OO

---

### Post by Cephyr on 2006-01-23
Ditto to the above. I run Ubuntu on a 633 Mhz Pentium III and it's just as fast as my Dad's 2 Ghz windows machine.

---

### Post by Dragonbite on 2006-01-23
I have a PIII 500MHz maxed out with 256MB Ram (Sony Vaio desktop I got around 2000) and I haven't installed Ubuntu yet, but I have fooled around with Gentoo.

Even then, I have run (slowest to fastest) KDE, Gnome, Xfce and Fluxbox. If you are looking for something to be instantly responsive like a 3GHz machine,  nothing's going to work.

If you are patient, any of these will work but I have to concur that Xfce is probably the best option.  It balances some of the utilities for the desktop environment (something window managers like Fluxbox doesn't do) without the same "drain" as Gnome or KDE.  All this without loss of options for programs to run (Abiword, Open Office, etc.)

Also make sure you turn off any services you are not going to be using.

As soon as I'm done getting by more "up-to-date" machine (it's twice as powerful as my Sony... 1GHz, 512MB Ram, etc.) running nice and smoothly then I'm planning on setting up the Sony with Xubuntu!

Until then, I leave it running using the live CD.

---

### Post by az on 2006-01-23
[QUOTE=Dragonbite]

Even then, I have run (slowest to fastest) KDE, Gnome, Xfce and Fluxbox. If you are looking for something to be instantly responsive like a 3GHz machine,  nothing's going to work.[/QUOTE]

Ubuntu is more responsive on my 700 Mhz machine than on my father-in-law's 2.4 Gig windows box.

---

