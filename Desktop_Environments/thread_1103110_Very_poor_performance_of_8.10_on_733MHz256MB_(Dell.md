---
title: "Very poor performance of 8.10 on 733MHz/256MB (Dell GX110)"
date: 2009-03-22
forum: Desktop Environments
---

### Post by Cubytus on 2009-03-22
Hi there, 

this second topic is to know how I can achieve decent performance on this configuration under Xubuntu 8.10. Typically, using Windows 2000 as a reference, reaction time with Firefox and just opening files and directories is not snappy, but quite fast. Under Xubuntu, it's sluggish: just clicking on another window to give it focus takes about 3 seconds, same when switching tabs, etc. Lauching a new application can take between 30 seconds and 1'30" (!).

I already modified the **/etc/hosts** file, and that didn't changed anything. After that, I tried with a manual Debian+XFCE install, and results were basically the same.

As symptoms, CPU is not constantly 100%, but quite high, never under 30% when FF is running (I assume it's normal, since FF is not exactly the most CPU-frugal program known, especially on older computers). Launching a new application doesn't always make CPU work hard; many times the interface hasn't appeared yet, and the CPU is back to baseline.
Doesn't seem like a saturated CPU problem.

The other symptom is the RAM, which on the other hand seems constantly saturated. The result is high swapping, which puts a heavy performance hit on such a slow hard drive. But I'm unsure about if this causes low reactivity.

Any help would be appreciated.
Thx

---

### Post by snowpine on 2009-03-22
Hi Cubytus,
First of all, Windows 2000 vs. Xubuntu 8.10 is not a fair comparison--you are comparing an 8 year old OS with a modern OS. They have very different minimum hardware requirements. 

I would recommend a lightweight distro such as DSL, Puppy, or SliTaz for your computer. Your computer's specs are pretty much the bare minimum for Xubuntu, which is why it's struggling. If you really want to stick with Xubuntu, I highly recommend 1) a lightweight windows manager such as fluxbox, openbox, jwm, etc; 2) a lightweight web browser such as kazehakase, dillo, etc.

---

### Post by Flash858 on 2009-03-22
I agree with the above - On that configuration, try Puppy 4.2 Deep Thought with the default SeaMonkey browser. I have it on a PIII laptop w/192MB (also designed for Win2K) and it flat out flies!

[www.puppylinux.org](www.puppylinux.org)

---

### Post by linuxrollup on 2009-03-22
Although (K)(X)ubuntu requires you to have at least 256MB RAM, you should have a swap partition. How big is it? Also, I'm not sure of the CPU saturation issue you've got. Sorry!

---

### Post by hictio on 2009-03-22
Can you increase the RAM on that box?
And, on Linux it is perfectly normal for the system to use all the available RAM, what's the point of having it if you aren't using it? :)

---

### Post by Cubytus on 2009-03-22
Well, the OS itself is sure more recent, but Xubuntu is supposed to be a noticeably lighter version of Ubuntu, usable on smaller configs. To what point a smaller config is considered "modern" enough to use on a current generation OS, I'm really not sure, but I still don't consider 733MHz as pure crap for basic tasks. This computer of course has a 486MB swap partition (otherwise it would simply crash, running out of RAM - I would have prefered a cleaner solution with the OS asking to quit a tab/program to free up RAM unless willing to take a big performance hit). On another forum, one user with the same computer clearly stood that this performance would be normal for a 300MHz, not a 733, but didn't found any explanation to it.

I had experience with **DSL and Puppy**, but found that these distros were not quite what I intended them to be; DSL never recognized USB drives properly when I tried it on an even older Pentium 133 (I managed to put a USB card inside!), and I was never too found of Puppy's interface. I guess that's customizable, but I just wanted to use the system, more than tweaking it. And "proprietary" (i.e. not used anywhere else) package formats were definitely a deal breaker: I needed to re-pack software in the first place, since community is not very active at maintaining repos. It would take hundreds of megabytes just to repack the softwares, space I didn't have since hard drives were the same generation as the rest of the machine (Not more than 2GB). That was like 2 years ago.

I also don't want to use anything else than **Firefox**, for the sake of standardization: I use **Zotero** all the time, on any platform I happen to be. Dillo is especially not a good choice (Unstable, bad rendering of many sites).

The **RAM** is there to be used, of course, but **swap use is best avoided**; therefore, before swapping, the OS should be frugal with RAM in the first place, by not loading so much unnecessary modules; I would rather have a slower new application start-up and a snappy OS and basic app than a sluggish start-up and permanently slow OS. Swapping should be a last resort. Unfortunately I cannot add RAM in this machine simply because I don't have any big modules left in PC133 format; smaller modules I have are buggy, and the computer wouldn't start with them attached.

I could use **FluxBox**, and hope it's more user-friendly than it used to be. I admit, my reference in usability is GNOME, but I noticed Linux programmers and users are sometimes different just for the sake of it. I also happen to use some GNOME apps, and I hope that using FluxBox wouldn't use up too much disk space on top of GNOME libraries.

**Bottom-line** is, well, I'm an end-user. Willing to discover new things, but no fighting against the machine/spending hours trying to figure out how to do simple tasks, especially not on a back-up computer (too noisy and low-performing to stay on as a server - plus it doesn't support SATA drives)

---

### Post by kerry_s on 2009-03-22
it doesn't have to be slow, but you do have to work at it.
fluxbox will definitely help, anything is better than a full desktop on that much ram.

> Bottom-line is, well, I'm an end-user. Willing to discover new things, but no fighting against the machine/spending hours trying to figure out how to do simple tasks, especially not on a back-up computer (too noisy and low-performing to stay on as a server - plus it doesn't support SATA drives)
 

are you sure linux is what your after?

i'm using a 10 year old laptop, 450mhz 256mb ram, its setup for maximum performance, i use a light window manager(jwm) to keep the resource use low so it can be used for the more important apps like the web browser(firefox). i usually don't dip into swap unless i use the office suite(open office) and it's only a few mb of swap.

---

### Post by Cubytus on 2009-03-22
> **kerry_s said:**
> 
are you sure linux is what your after?
Absolutely. I switched from the other OS to Ubuntu 3 years ago, and still don't intend to run back. In the beginning I simply grew tired of constantly defragmenting, disinfecting and generally pirating software just to get a usable box that needed to be reformated every year anyway.

I gave Ubuntu a chance, being told its usability and community support was amazing, which is true, most of the time, plus doesn't needs pirating. On the other hand, I had a bad experience trying to find an affordable and sturdy no-OS or Ubuntu laptop, and current sellers usually have slow, expensive or plain ugly/heavy machines. For the OS itself, there was still unresolved issues - no way to manually control fans (noisy), unexpected Brasero crashes, VLC not quitting properly, bad screen detection (seems everyone has this problem in a form or another), hibernation and standby crashing on wake-up, and generally slow OS for the hardware (Athlon 64 3200+1GB).

Now the box is dead - needs a quality power supply and probably a motherboard, Montreal area ;) - I went with a MacBook Unibody, following positive experience I had with friend's Macs. It's not without flaws, Apple acts cheap, but the OS and technical service are both excellent, and doesn't have issues I defined. I definitely couldn't live on a laptop without hibernation.

Given another modern desktop machine (or $300 to build it - no needs of fancy graphics card, scren or additional optical and hard drives), I will use it under Ubuntu since the OS is updated so often.

> i'm using a 10 year old laptop, 450mhz 256mb ram, its setup for maximum performance, i use a light window manager(jwm) to keep the resource use low so it can be used for the more important apps like the web browser(firefox). i usually don't dip into swap unless i use the office suite(open office) and it's only a few mb of swap.
Then, do u have some screenshots of **key parts of your GUI**, just so I can see what are the equivalents of, say, **Synaptics**, **Settings panel**, **log viewer** (no simple text editor, plz: I want to be able to see what logs are being updated when an action is performed - GNOME's log viewer allows this), how the **menus** are organized and how do you **install other binaries**: what **package format** is preferred for, say, installing Skype? (No argument on this one)

And how does it compare to FluxBox?

---

### Post by utnubuuser on 2009-03-22
I've just installed Debian Lenny on a P3 with 256megs ram.

My processor is a bit better than yours, but not by much.

I couldn't get Ubuntu to install no matter what I tried, and I only got debian on by using the alternate cd with a minimal install, then adding xorg and gnome-desktop.

It's doing ok now.

I was disappointed at the fact that Ubuntu wouldn't install past the kernel loading Window, but I figure with a little extra ram it'd probably take.

It sounds as though your machine might have some other issue.

---

### Post by hictio on 2009-03-22
> **utnubuuser said:**
> I've just installed Debian Lenny on a P3 with 256megs ram.

My processor is a bit better than yours, but not by much.

I couldn't get Ubuntu to install no matter what I tried, and I only got debian on by using the alternate cd with a minimal install, then adding xorg and gnome-desktop.

It's doing ok now.

I was disappointed at the fact that Ubuntu wouldn't install past the kernel loading Window, but I figure with a little extra ram it'd probably take.

It sounds as though your machine might have some other issue.

I have a Pentium II @ 333 MHz with 512 MB of RAM, and I had to install like that, meaning from the Alternate CD, doing a minimal install, and then install Gnome via aptitude from the repositories since 8.04.
On Juanty, using the Alpha 6 release, that didn't work, tho.

---

### Post by Cubytus on 2009-03-22
Well, the machine may have other issues, too, as sometimes USB keys wouldn't mount, giving an error, the optical drives not working. It's almost entirely recycled components, after all.

---

### Post by kerry_s on 2009-03-22
> Then, do u have some screenshots of key parts of your GUI, just so I can see what are the equivalents of, say, Synaptics, Settings panel, log viewer (no simple text editor, plz: I want to be able to see what logs are being updated when an action is performed - GNOME's log viewer allows this), how the menus are organized and how do you install other binaries: what package format is preferred for, say, installing Skype? (No argument on this one)

when i used debian i used synaptic to, there's no substitute, most of the time i would use apt-get in term, but did use synaptic when i felt like seeing it. currently i use arch linux, it has pacman, so the gui is the terminal.

settings for the gui i use lxapperance, simple and very light.

logs, i have syslog disabled, don't care for the extra cpu cycles. if i wanted to view logs, i would use the terminal or the editor. some things still log, but only on startup or use.

skype, in arch i just check to see if it's there and install it. i have alias's set up for the commands, i use s for search and i for install.

---

### Post by Cubytus on 2009-03-23
there, a smallupdate: I'm trying Openbox. 

For the bad news, although I installed everything from the repository, it seems the instalaltion is broken. Logging it after changing the session, only "Openbox session" works, not "Openbox-gnome". As far as the performance is concerned, I kept a Terminal with htop open and running while using Firefox. The good news is, swap is not used imediately on opening, but FF is still very heavy. At least the windows manager doesn't take more resources that it needs to.

Still, FF and Synaptic reactivity is poor, but still can't explain why: CPU barely goes above 50% running **both** applications, and swap only gets used at 10 to 20 MB, which is low even for such an old beast.

---

### Post by hictio on 2009-03-23
Don't know if you saw these, but if you didn;t, they might come handy:

. [Installation on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
. [Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by Cubytus on 2009-03-23
These pages are more complete than last time I looked at them. But I cannot attempt to reinstall now, since the optical drives are not working (seemingly).

Openbox install itself seems broken: although I installed everything (just to start safe) defined with the keyword "openbox" in Synaptic, I ended up with a brown-background desktop with absolutely nothing on it, not even a task bar. A right-click menu allowed access to a terminal. "openbox-gnome" session doesn't even start.

Currently, even LXDE does take quite a bit of swap with FF open (around 200MB)

I must have missed something.

---

### Post by kerry_s on 2009-03-23
i don't know, kinda sounds like you got hardware issues.
do you think your drive could be ready to go out?

---

### Post by snowpine on 2009-03-23
> **Cubytus said:**
> 
Openbox install itself seems broken: although I installed everything (just to start safe) defined with the keyword "openbox" in Synaptic, I ended up with a brown-background desktop with absolutely nothing on it, not even a task bar. A right-click menu allowed access to a terminal. "openbox-gnome" session doesn't even start.


That is the correct behavior for Openbox. It does not have any background or task bar, just a right click menu. That is why it is so light on resources. :)

The Gnome/Openbox session option only works if you have also installed Gnome. You should choose just plain Openbox from the session menu (assuming you like Openbox; sounds like it may be too minimalistic for you). 

If there's a panel/task bar you like (lxpanel is popular), you can have it auto-start by adding it to your ~/.config/openbox/autostart file. Check out Crunchbang (#!) Linux if you want to see what's possible with a well-configured Openbox over an Ubuntu core.

---

### Post by Cubytus on 2009-03-24
Well, I can't really go to Crunchbang this this would require at least a working optical drive.

On the current OpenBox setup, lxpanel is indeed manual starting. I put it in **/.config/openbox/autostart.sh** file. Don't know yet how to start Conky and stick it to the background.

And finally, the base problem is unsolved; the system still reacts sluggishly, wether or not swap is used; it's just worse when swaps kicks in, after hours of uptime.

---

### Post by Flash858 on 2009-03-27
I don't know when you last tried Puppy Cubtyus, but dillo? That was forever ago, and only on a few obscure distros.

Puppy Deep Thought has SeaMonkey (as have most Puppy distros), and if you can't make Puppy work for you, I would definately go back to an older version of Windows, like 98.

Here is a screenshot of my desktop install, though my laptop looks identical, save for the screen resolution, it being a bit squarer, as it is not a widescreen format.

With a PIII 700, 192MB of RAM, a 1 GB swap file and a 40 GB drive partitioned for Puppy, Win XP, and Xubuntu, it is still a very viable computer, and there is little I cannot do in Puppy. I keep the other 2 OSes on there for my girlfriend (Windows) and for compatibility with a few desktop files (Xubuntu). Also, I have cool Ubuntu stickers all over the laptop, so it just would not be right to not have it installed ... ;)

[http://hiltonheadphoto.com/screenshot.jpg](http://hiltonheadphoto.com/screenshot.jpg)

---

### Post by Cubytus on 2009-03-27
Well, for Dillo, it was under DSL, to be exact. Puppy had SeaMonkey, but I still disliked Puppy's ergonomy, and I remember SeaMonkey was behaving slightly different from Firefox (Maybe an old habit from Ubuntu...).

I admit your Puppy looks great, but how far is it functional, and how much time did you spend configuring it? I also remember this Linux flavor was not easily localizable, and that localized versions were constantly late on the reference one.

I consider USB keys/CDs automount and running OpenOffice, Firefox for an OS to be usable for my needs

Also, what package format is used under the current Puppy? I don't want any obscure format like DSL uses.

There's no way I will use a deprecated and incompatible OS such as Win 98. 700MHz where mainstream (affordable) around 2000-2001, and relatively modern OSes such as Win 2000 and XP (still the reference in Redmond-made OSes) where built for these CPUs. I just don't want to pirate and patch Windows anymore.

But from your post, what I understand is you have a good and reactive computer that is slightly under the specs of mine. Am I wrong ? Or you still occasionaly use a sluggish Xubuntu for the sake of compatibility? Oh, btw, what are those "incompatible files" you need to keep Xubuntu for ? But 1GB swap on a laptop hard drive must me a real pain to deal with? What is your typical RAM/swap used in a normal, multi-tasking environment?



Last, for your girlfriend... You should probably educate her concerning Puppy's compatibility and dump that other OS, unless it makes the computer more reactive :lolflag: :(

---

### Post by andso on 2009-03-30
hi cubytus
try with this in /etc/hosts  file
127.0.0.1 localhost **name**
127.0.1.1 name  

by gksu mousepad /etc/hosts  in the terminal

Edit: i suppose you haven't a domain name

---

### Post by Cubytus on 2009-03-30
Already done, as said in one of my preceeding post. No change in slowness.

By the way, I recently used it with only SANE and Firefox Open on my router's webpage, and a terminal with htop. The swap did not kick in, yet it was still feeling sluggish. CPU use was below 50% at all times.

---

### Post by Jallu59 on 2009-03-31
There must be something wrong with your Openbox installation. Could there be something left from the Xubuntu installation that slows down the system.

I have got an F-S laptop with 450MHzP3 & 192 MB ram which i am running with LXDE-desktop installed on top of Ubuntu 8.10 CLI. The system uses only 86MB ram while running firefox and uxterm(terminal). The firefox starts within 15 seconds.

Yours
Jari J. Lehtinen
an elder PC-pro from Turku, Finland

EDIT: Your motherboard accepts 2x256MB=512MB ram. I suggest you to do the upgrade.

---

### Post by Cubytus on 2009-03-31
So, I should reinstall xubuntu from scratch in command line mode (alternate install) and add OpenBox on top of that? Or directly use the OpenBox variant of Ubuntu?

Or, is there a simple way to get it working without relying on optical drives?

Thanks!

---

### Post by adamlau on 2009-03-31
Ubuntu Minimal + Openbox would be the way to go in your case. The alternate install only provides a lighter install interface, but is just as bloated as the standard install.

---

### Post by Cubytus on 2009-03-31
So, I need to :
1- download an Alternate Install image
2- burn it on CDRW
3- Install in command line
4- manually add OpenBox? or manually add XFCE, hoping it will be lighter than standard Xubuntu?

Is there a way to avoid using an optical drive? I have a Mac OS X on hand to help if usable...

---

### Post by kerry_s on 2009-03-31
> **Cubytus said:**
> So, I need to :
1- download an Alternate Install image
2- burn it on CDRW
3- Install in command line
4- manually add OpenBox? or manually add XFCE, hoping it will be lighter than standard Xubuntu?

Is there a way to avoid using an optical drive? I have a Mac OS X on hand to help if usable...

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
has pics and all.

you must be doing something wrong, cause i'm just know doing a setup on 700mhz 128mb ram, minus the vid, i'm working with 122mb ram.

---

### Post by Flash858 on 2009-05-02
Cub - I mostly keep Ubuntu (now Ubuntu Lite) on the laptop because it is covered in Ubuntu stickers... 

I have not tried making .pet packages yet, so the "File compatibility" I spoke of is in reality the Tux Racer game that I'm addicted to (OK, you got me...I'm out of the closet...).

You may want to try Ulite, as it runs twice as fast as Xubuntu, albeit with a lot less functionality, but I still SWEAR by Puppy for a myriad of reasons. It is TOTALLY functional, and there are utilities in it unique to Puppy I cannot live without. It is also great for fixing things in other distros, as you have total GUI root access.

As far as my desktop is concerned, all I did was change a couple widgets, the wallpaper, and the icon set. Everything else is "stock".

Puppy flat out rocks...After Ubuntu, it is my absolute favorite OS. Clean, simple, lightweight, functional, very unique, asthetically appealing, totally customizeable,...Other than that, it it terrible...LOL...

---

### Post by Cubytus on 2009-05-25
Finally. I upgraded to 9.04 through the update interface. Was slow as hell, taking more than 2 hours to install, but seems to be functional, er, as slow as usual. [I had another bug]("http://ubuntuforums.org/showthread.php?t=1168989") that is not a deal-killet, but still, is a bug.

Optical drive is still dead, so converting to an entirely different distro using my limited knowledge is not likely to succeed.

Bottom line is the machine is still slow as hell

kerry_s, is 122MB your used RAM, or your available RAM? As usual with old computers, swapping is a huge performance hit.

---

### Post by quadproc on 2010-02-27
Cubytus has a slow running system:
> **Cubytus said:**
> 
As symptoms, CPU is not constantly 100%, but quite high, never under 30% when FF is running

When I was running Ubuntu 8.10 on a well equipped system I had noticed that the CPU usage was always a minimum of about 30%, regardless of what was going on.  I was wondering if the 8.10 kernel was doing some kind of polling to keep it that busy when it should have been idle.  When I switched to version 9.04 the CPU usage went to near zero during idle times.  In fact, the only thing that seems to get 100% CPU usage is printing - maybe that is using polling on its parallel port.

> 
The other symptom is the RAM, which on the other hand seems constantly saturated. The result is high swapping, which puts a heavy performance hit on such a slow hard drive. But I'm unsure about if this causes low reactivity.

It certainly could.  There are so many factors involved in that problem that I could not begin to guess which ones might be involved.  Things such as the real time clock interrupt rate being too slow could throw a wrench in the works because it would slow down task switching when IO is infrequent.


I happened upon this thread because I am planning to upgrade a P3 800 MHz system with only 256 MB of RAM to a decent OS (it presently has NT) and I am finding that the computer won't boot from a live CD: it reports a bad CRC when I try to read it in that system even though the CD works fine in other systems.  If anyone can suggest a way around this, I would appreciate it.  Thanks.

quadproc

---

### Post by Cubytus on 2010-02-27
> **quadproc said:**
> When I was running Ubuntu 8.10 on a well equipped system I had noticed that the CPU usage was always a minimum of about 30%, regardless of what was going on.  I was wondering if the 8.10 kernel was doing some kind of polling to keep it that busy when it should have been idle.  When I switched to version 9.04 the CPU usage went to near zero during idle times.  In fact, the only thing that seems to get 100% CPU usage is printing - maybe that is using polling on its parallel port.I don't remember 8.10, but 9.04 keeps the CPU idle when actually nothing is being done with the computer. I also can't reproduce your issue of 100% CPU use for printing, although I also use a parallel port printer w/ polling.


> It certainly could.  There are so many factors involved in that problem that I could not begin to guess which ones might be involved.  Things such as the real time clock interrupt rate being too slow could throw a wrench in the works because it would slow down task switching when IO is infrequent.I can't figure how does this relate to RAM saturation.


> I happened upon this thread because I am planning to upgrade a P3 800 MHz system with only 256 MB of RAM to a decent OS (it presently has NT) and I am finding that the computer won't boot from a live CD: it reports a bad CRC when I try to read it in that system even though the CD works fine in other systems.  If anyone can suggest a way around this, I would appreciate it.  Thanks.Don't waste your time with that system. I'm even planning to convince my father to dump its inefficient 1,6GHz "toaster" P4 / 512 MB.

Calls for anything optimization-related made to respect scarce resources in the perspective of multitasking are ignored or outright muted, as my personal experience shown, and using a 11-year-old computer with a 6-month-old OS and applications isn't likely to succeed comfortably, except perhaps in text mode.

The CD drive seems to be dying; find a replacement, it's just not worth the trouble.

---

### Post by efflandt on 2010-02-28
I got an old PIII 550 from work and scrounged up some P100 RAM from another old computer to bring it up to 512 MB.  Since its BIOS predated 1999, I had to add kernel parameters "acpi=force" for acpi and "lapic" for it to fully power down.  It has a real video card, although, I think I used xorg-driver-fglrx.

Flash had a slow framerate in Ubuntu 9.04 or 9.10 and Kubuntu 9.10 seemed worse.  So I installed Qimo for kids (based on Ubuntu 8.10) and gave it to my niece for her 4 year old twins.  It works fine with children games.

I first used Linux when hard drives were smaller than 256 MB.  Now 256 MB is not really enough RAM to run a full blown Linux system efficiently (or WinXP) even on a P4, especially if you have integrated video with shared RAM.  Although, I have been running an old Linux version on a headless (monitorless) Celeron 300 as a server in my basement for many years on much less (uptime not posted because it starts over from zero within 498 days).

```
efflandt@realhost:~> free -m
             total       used       free     shared    buffers     cached
Mem:           155        151          3          0         51         11
-/+ buffers/cache:         88         66
Swap:          361          7        354

efflandt@realhost:~> cat /etc/SuSE-release 
SuSE Linux 8.2 (i586)
VERSION = 8.2

efflandt@realhost:~> ls -l /var/log/boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        20461 2006-07-20 16:00 /var/log/boot.msg
-rw-r--r--    1 root     root        24670 2006-07-20 04:45 /var/log/boot.omsg

efflandt@realhost:~> uname -a
Linux realhost 2.4.20-4GB #1 Tue Mar 29 13:05:16 UTC 2005 i686 unknown unknown GNU/Linux

```Mozilla is downright snappy in KDE of SuSE 8.0 on my old PIII 500 laptop with 192 MB RAM.  So it should still be possible to find a workable lght system for 256 MB RAM, I just have not checked them out yet.

---

### Post by aklo on 2010-02-28
Although xubuntu is the lightest ubuntu os out there, your hardware is also seriously outdated.

Even my netbook is faster than your pc and with your pc specifications, even a netbook edition ubuntu will be slow.

I recommend you to get more ram first. I've been though upgrading my 64MB ram to a 320 ram and the performance boost was amazing.

Your applications use memory first, if your memory runs out, it goes to your harddisk and there is where your OS begins to crawl.

On a side note, my conky shows ubuntu 9.10 using about 220MB ram on startup without any other application running. So 256MB memory with good performance....good luck.

---

### Post by quadproc on 2010-02-28
> **Cubytus said:**
> 
I can't figure how does this relate to RAM saturation.

The quoted question/comment was related to my statement that a real time clock running at too slow an interrupt rate could cause poor performance.  I had not intended to get into detail in my original post but since there seems to be some interest I will elaborate below.  My original goal was to show how some unobvious things might be involved in the poor performance problem.

So, on to an explanation.  Most personal computer systems today use a conventional interrupt driven task scheduler.  The sources of interrupts can be many, but a major source when the system is active is IO.  Whether the system is idle or busy there is usually a periodic interrupt from a real time clock; this may be programmed to various rates but rates between 10 and 100 times per second are popular.  Assume for the moment that the system's current task mix only involves a single IO from a single device.  If the system is just sitting there waiting for something to happen (say for example for that IO to finish but something is wrong with the IO so that it never finishes) then the task scheduler will not wake up until the next real time clock interrupt happens.  If the RTC had been set to only one tick per second then it would be up to 1 second before the system would react to the failed IO.  The failed IO might or might not succeed on a retry so the human observing the process might or might not be alerted to the failing IO problem, but he or she would notice that things had really slowed down.  If the RTC were set to 100 intrrupts per second then the maximum time for the task scheduler to react would be 10 milliseconds and that amount of time would not be noticed by a human.

In reply to the RAM saturation issue, no, there isn't any direct relationship between that and the RTC rate.  But there could be a relationship between slow response and the RTC rate.

I hope that my explanation makes sense.

quadproc

---

### Post by RJARRRPCGP on 2010-02-28
The issue of taking 3 seconds to focus on a window, sounds like you need more RAM.

---

### Post by Cubytus on 2010-02-28
> **aklo said:**
> 
Your applications use memory first, if your memory runs out, it goes to your harddisk and there is where your OS begins to crawl.

On a side note, my conky shows ubuntu 9.10 using about 220MB ram on startup without any other application running. So 256MB memory with good performance....good luck.Fact is OSes have grown to unwieldly weight without doing much more than in 1999. Where I could use an arguably spartan Win 2k Pro reasonably fast on 128MB RAM, even Damn Small Linux can't do any better although it's supposedly "lightweight". Add another 200MB for Firefox on top of that (FF is now the standard for anyone wishing to enjoy the Web as it's meant to be), and your computer is crying for help.

With such a setup (Ubuntu+Firefox running), 512MB is barely enough.

Optimization is largely being ignored nowadays, developpers and users alike prefer to use the canned answer "get more RAM", instead of trying to understand why 1GB in 2010 is considered insufficient, although it was plenty, 4 years ago, with basically the same usage pattern?


quadproc> That makes sense now, thanks :) 
I still have another question, though, as it seems Ubuntu and Xubuntu may share a slow-rate RTC. RTC standing for Real-Time, how come Ubuntu is much faster on better hardware, much more than the raw processing power increase?

---

