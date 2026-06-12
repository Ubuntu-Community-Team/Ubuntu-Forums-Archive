---
title: "ATI Drivers?"
date: 2009-02-18
forum: General Help
---

### Post by valros on 2009-02-18
Im a big Nvidia fan, always used their cards and have found excellent support for Linux. Im about to upgrade cards and the price vs performace difference between Nvidia and ATI cards is tempting. The only factor I've so far left out are the Linux drivers, how far have ATI's drivers come, many threads I read are a few years old and are such outdated. Is there significant performace/stability/customization in ATI's drivers? (at least comparable to what Ive found with nvidias)

---

### Post by valros on 2009-02-19
Can anyone give some insight? How are the open-source ATI drivers?(4850)

---

### Post by Yashiro on 2009-02-19
Both sets of drivers are equally terrible. :D

At the moment in Ubuntu 9.04 my 4850 still doesn't get recognised or configured properly using the open source drivers.
In Ubuntu 8.04 I'm using the latest 9.1 Catalyst drivers. 
Once you do get them installed, which sometimes can be tricky, they work OK as far as Linux goes. They have never crashed in use, either on the desktop/compiz or while playing Quake. Desktop performance is almost as fast as Windows/Mac.

While not entirely related, my other machine runs Debian 5.0.
The nvidia card in this box runs OK but with very poor compiz performance using the repository provided drivers. Switching to the newest nvidia drivers I gained alot of performance but gained an issue of the desktop not loading after a reboot :).
I can install the drivers and restart X fine as many times as I like, but as soon as I reboot the machine hangs. 
This is very likely a simple issue related to the kernel module. However, it's just a spare machine for random testing so I reverted to the repository driver until I get the urge to look into it.

Generally, and historically, Nvidia have provided better performance on Linux.
But like I stated in my opening line you will find as many complaints against Nvidia as you do against Ati these days.

---

### Post by Insane1 on 2009-02-19
> **valros said:**
> Can anyone give some insight? How are the open-source ATI drivers?(4850)

The open source ATI drivers have actually improved alot from ye olden days, and seem to improve with every release. At the moment, my X1400 Mobility 128mb gets 3D acceleration now (some programs won't use some shaders, however, such as SecondLife. Which means none of the miracle prim glow that was introduced with the windlight client), and can play a few games just fine (such as Nexuiz and Open Arena) with very limited slowdown as opposed to once upon a time. In some ways they are also more stable than the proprietary drivers, which have occasionally given me an unending 'screen blink' while watching youtube, requiring me to ctrl+alt+backspace out to the login screen.

Not much else I can personally say, aside from giving some glxgears results I've gotten over the past few months.

Around Ubuntu 8.04 at first release, GLXgears with the open drivers gave me a performance of about 400fps. With Ubuntu 8.10, it's increased to 900 or so average (and growing with each update), and the perfomance increase is quite noticable. The proprietary drivers give an average of about 1200-1400fps, and do indeed work faster and smoother with 3D acceleration (as well as allowing shaders to be used in programs such as Second Life), but have the problems I mentioned before such as 'screen blink' (Not sure if that's a problem unique to my laptop, or if that's common).

Note that my screen resolution is 1280x800, and I'm using glxgears as it starts up from command line in a window (not maximized).

EDIT: Note, when I say proprietary, I mean the Hardware Driver's installed fglrx, not the one from the official site (which, to tell the truth, I'm a little frightened to try installing).

---

### Post by rootkowski on 2009-03-02
I changed from nvidia to ati some months ago and that's pretty much when my headaches started. The flickering/screen blinking was quite unbearable, tremendous graphics corruption when trying(!) to play games in wine (I never really got to playing games using ati drivers). I wasn't satisfied with the open source drivers, but the problems described above I had with ati's drivers. I've even got to the point where I don't mind uninstalling older and installing newer drivers from ati. Yet it hardly gets better with new releases. When they finally fixed the flickering, they introduced problems with scaling video (version 9.1). Now they say they fixed the scaling issue (not in my case!) the performance is quite poor (unless I did something wrong reinstalling the driver last time; I used to get above 4000 fps with glxgears on my radeon x1950, now it's 75!).

Phoronix has a lot of performance tests etc. which might be interesting for you to look through. My advice would rather be to stick to nvidia and use slightly older drivers (you can read about it [here @ Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=NzEwMQ")).

Cheers!

Edit: I changed some settings in Catalyst Control Centre and now the performance is much better (above 8500 fps!). The problem was that I had vertical refresh set to "On, unless application specifies".

---

### Post by emarkay on 2009-03-02
I have the ATI drivers on my other PC and they seem to work fine.  I use the Omega variants for Windows and the proprietary driver in Ubuntu. 

I had all kinds of strange problems getting the Open Source driver to work correctly - of course I am driving a 720P HDTV, so it "sort-of-has-to-work" "out of the box "or I get no video image...

---

