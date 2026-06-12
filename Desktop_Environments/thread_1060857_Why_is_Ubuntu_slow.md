---
title: "Why is Ubuntu slow?"
date: 2009-02-05
forum: Desktop Environments
---

### Post by uid313 on 2009-02-05
I have a good computer. Core 2 Duo, 4 gb RAM, GeForce 8600GT, 7200 rpm disk.

When I open gedit or gcalctool it takes 1-2 second.
Not much, but its 1-2 seconds too much.

One thing I noticed with Windows XP is that it is blazing fast. When I open notepad or calculator, it opens in an instant before I even can blink. No delay.

Why is it that Ubuntu is slow to start applications?
Does GNOME suck?
Is GTK+ to blame?
Is it Xorg?

---

### Post by snowpine on 2009-02-05
Hi Uid313, Windows XP is almost 10 years old and has much lower hardware requirements than Ubuntu; that is why it's faster. :)

You can use the command 'top' from the terminal to see what is tying up your memory and processor... Lots of tips for speeding up Ubuntu. My favorite is to go to System->Sessions and disable any startup services I don't need, like bluetooth or tracker. This can really make a difference. I also personally don't use Gnome; I find that a window manager such as openbox or fluxbox gives better performance. If you are new to the world of windows managers, LXDE is a very easy alternative to Gnome. Good luck!

---

### Post by malachi1990 on 2009-02-05
What version of ubuntu are you using? 

Possibly related is that I noticed a significant drop in speed right after upgrading to Hardy, and sudo broke in the upgrade. Once I fixed sudo, it sped up incredibly.

And no, GNOME doesn't suck, though it does have it's annoyances.  

Make sure that you have the correct video drivers installed if you're using compiz, as that also sped up my computer.


@snowpine
On the three computers I've installed ubuntu on that had XP as the OEM, ubuntu was noticeably faster as a fresh install (a 512 mb laptop, a 384 desktop and a 512 desktop).

---

### Post by taurus on 2009-02-05
Are you running x86 or x86_64?

---

### Post by uid313 on 2009-02-05
I have noticed this slowliness in all versions of Ubuntu.
I am currently running 9.04 Jaunty Jackalope (beta).

I am using the proprietary Nvidia device drivers.

I am running x86. I am planning to switching to x86-64 though.

---

### Post by mcduck on 2009-02-05
The more complex (and feature rich) way graphical desktop is implemented in Linux causes a bit more delay when starting programs than what you get in Windows. However this only makes the program start a bit slower, and doesn't mean the OS itself would be slower, usually quite the opposite.

I undertood that this is what you are complaining about, slow opening of programs, not actually slow working of the OS or programs?

Another thing is that Windows preloads some of it's programs to memory during startup, this slows the system boot but makes stating those programs the first time take less time. The downside, of course, is that this only applies to some Microsoft's own programs like IE and Office, and of course people might not even want to use them which only leaves those people with slower boot time..

---

### Post by warp99 on 2009-02-05
You can use a program called preload that will read ahead cache commonly used programs. More info here:

[http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html](http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html)

I'm not sure if this is set by default in Jaunty, try searching the forums a little to find out. ;)

Edit:

Here's a paper by the developer Behdad Esfahbod explaining preload:

[http://ubuntu-debs.googlecode.com/files/preload.pdf](http://ubuntu-debs.googlecode.com/files/preload.pdf)

---

### Post by adamlau on 2009-02-05
Most of us have tried everything we could to optimize the system for speed. From config entries to disabling unnecessary services to compiling the kernel and userland apps from scratch, nothing you can do will speed up Ubuntu to the point of appreciation, short of going with a minimal install and a lightweight desktop. Bear in mind that you are not alone in your concerns. Your good box is actually my slowest box and I am still not satisfied with system response on a minimal install + JWM :( .

---

### Post by mcduck on 2009-02-06
Honestly, though, Ubuntu is still starting programs quicker than OS X, for example. Actually Ubuntu with all the nice effects enabled, running on my 3-years-old laptop is more responsive than 1-year-old iMac. ;)

And, like I said, the difference when compared to XP is only in program starting times, when actually doing something with the programs Ubuntu beats XP. Personally I rather wait 1 sec more to load the program if it then does the task in less time.

---

### Post by adamlau on 2009-02-06
Ogghand, my tuned and stripped iMac Core Duo feels faster than my tuned and stripped Ubuntu off similar hardware. Much faster, in fact :( .

---

### Post by adamlau on 2009-02-06
Offhand, my tuned and stripped iMac Core Duo (with a heavy emphasis on the use of the Rixstep ACP suite of tools) feels faster than my tuned and stripped Ubuntu off similar hardware. Much faster, in fact :( .

---

### Post by uid313 on 2009-02-11
I've noticed that when LXDE instead of GNOME, Ubuntu is much faster.

Perhaps this has something todo with the widget rendering engine?
Perhaps Murrine or whatever Human theme use is slow?

Maybe its GNOME or something.

---

### Post by adamlau on 2009-02-12
Your chosen desktop environment plays a role, as do the applications you choose to use. I have found that users who prefer lightweight environments tend to follow suit and use lightweight programs.  Regardless of whether they are on older hardware, or SSD/SCSI and quad cores. One of the easier featherweight environments for GNOME power users to transition to is JWM. Take a look at the [ArchWiki JWM article](http://wiki.archlinux.org/index.php/JWM) :) .

---

### Post by sharon.gmc on 2009-02-12
Yeah, I notice it to.  I am planning to change to Linux but I was thinking maybe there is a bug or something. . .

---

### Post by jrusso2 on 2009-02-12
> **uid313 said:**
> I have a good computer. Core 2 Duo, 4 gb RAM, GeForce 8600GT, 7200 rpm disk.

When I open gedit or gcalctool it takes 1-2 second.
Not much, but its 1-2 seconds too much.

One thing I noticed with Windows XP is that it is blazing fast. When I open notepad or calculator, it opens in an instant before I even can blink. No delay.

Why is it that Ubuntu is slow to start applications?
Does GNOME suck?
Is GTK+ to blame?
Is it Xorg?

It should not take two seconds to open a small app like Gedit.  Those should open quickly.  Things to check is your using the right drivers and they are configured right.  Check if anything is using a lot of resources that runs in the background.

---

### Post by thirdy on 2009-08-05
4-5 sec for me to open gedit from the terminal... I got a fresh Jaunty running on 2.4 Core 2 duo and 2gb of RAM.. And every window is getting dark all the time.

Ultimately the best OS for daily personal computing is Windows XP, although I'm a fan of Open Source (use a lot of open source in Java)..

But there's one negating factor to what I said w/c was the reason I'm back to using Ubuntu again. There was virus that closes Avira's Antivirus installer :P!

I'll try and use LDXE and see if nothing breaks else I'll consider to go back to xp :(

---

### Post by andrea000 on 2009-08-05
I have almost the same system but i have a 2.1 ghz processor
and my ubuntu system is blazing fast all my friends are jealous
I've tried to get them to go to ubuntu but they are scared :confused:

---

### Post by satish_j on 2009-08-05
I would recommend you to disable the Assistive technology from system menu->preferences,reboot and then check the performance.

---

### Post by Copernicus1234 on 2009-08-05
Its just one of the differences between the systems. Notepad is coded to be basically just a text box with no features. Try starting Microsoft Word... :)

Gedit in Gnome has lots more features than notepad so it takes a while to start.

---

### Post by galtthedestroyer on 2010-04-10
I have a 64 bit pentium 4 with 1GB ram running Lucid 64bit.  Windows 7 would slow to a crawl with multiple users logged in.  Ubuntu 9.10 was fine with all 3 household members loged in.  very fast in fact.  

somehow ubuntu changed.  so I upgraded to 10.04 beta 1.  then I did a fresh install of 10.04.  It's still horrible.  we're talking windows 3.1 from 1990 horrible.  I have to wait a few seconds when even right clicking something.  as soon as I log everyone else out, it's back to FAST.  

I've googled and googled but can't find anyone else with this problem.

---

### Post by stoush on 2010-04-10
hi galtthedestroyer,

i am hesitant to move to 10.04 just yet precisely for this reason. I have tuned my 9.10 just the way i like it. Even got a usb wireless key working and a customised compiled wine just to get some old games of mine going...

This is not helping with your problems I know, but could you share your current setup with multiple users?

cheers,

stoush

---

### Post by oOarthurOo on 2010-04-10
Anything different from the old setup? E.g., encrypted home on the new system. 

You might try some experimenting. Turning off desktop effects. Running nautilus in low-resource mode.

Many changes could be responsible for poor performance, from xorg, to the kernel, to new video drivers. Over time these issues will be resolved / workarounds discovered. 

At the moment however, if the Beta isn't working well for you I'd recommend sticking with the older releases that work well, until more users have gotten onto the new version. If you're not willing to be a ground breaker wait until a couple weeks after release and hopefully things will be better for you.

---

### Post by natravis on 2010-04-10
> **thirdy said:**
> Ultimately the best OS for daily personal computing is Windows XP, although I'm a fan of Open Source (use a lot of open source in Java)..

But there's one negating factor to what I said w/c was the reason I'm back to using Ubuntu again. There was virus that closes Avira's Antivirus installer :P!


I lol'd. Thanks!

---

### Post by gemmakaru on 2010-04-10
My C2D is only a 1.8 and running at 800MHz and everything is still fast to open.  Even the laptop drive isn't as fast as a desktop drive.  I would suggest settings are everything to do with this issue.  Trouble is there are probably a couple of billion combinations of settings and configurations so finding the right ones would be difficult.

---

### Post by praom2104 on 2010-04-10
I would recommend ubuntu tweak
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")
It may help you.

---

### Post by Rodney9 on 2010-04-10
I use Fluxbox for it's speed , simplicity and how easy it is to configure and gedit opens in less time than I can say " 1  second ".
You can see my setup in my signature.

---

### Post by cdude42 on 2010-04-11
I have Pentium duo-core at 1.6, 32-bit, 1GB RAM and i can open gedit in 1/2 a second running Lucid. not sure why everyone complains about the speed.

---

### Post by pneaveill on 2010-04-24
Currently running two machines on Jaunty and one one Intrepid (wife's school machine that she dares not lose anything from at all) and did a few of the recent security upgrades including FIrefox 3.6.3 or whatever it is and the machines run so slow.  I have followed the previous suggestions, but to precious little avail.  Any further ideas?

---

### Post by 3rdalbum on 2010-04-25
> **thirdy said:**
> 4-5 sec for me to open gedit from the terminal... I got a fresh Jaunty running on 2.4 Core 2 duo and 2gb of RAM.. And every window is getting dark all the time.

Check your system monitor - there must be a program running away with your CPU. Gedit takes 2 seconds on the first try and under 1 second in subsequent starts.

---

