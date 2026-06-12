---
title: "Bloat in Gnome. Get rid of it?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Azrael on 2005-10-19
In a fresh Breezy install and by *only* having the System Monitor open I see a sea of bloat. I'll list a few of the worst examples I see:

**clock-applet:** Uses **21.3** MB of virtual memory.

**gnome-cups-icon: **"When gnome-cups-icon is started it adds itself into your session. When any of your printers are printing, a icon will appear in the notification area to inform you of the printer’s status. As it has been added to your session you will not need to start it yourself when you start GNOME, this will happen automatically."** -- **Uses **36.8** MB of virtual memory.

**gnome-netstatus-applet:** "Network status applet for GNOME 2 GNOME panel applet that monitors network interfaces. It provides indicators for ingoing and outgoing data, packets received and transmitted, and information about the network interface itself such as IP information and Ethernet address." -- Uses **17.9** MB of virtual memory.

**mixer_applet2: **"enables you to control the sound volume on your system." -- Uses **20.3** MB of virtual memory.

**notification-area-applet: **Uses **16.6** MB of virtual memory.
**notification-daemon: **Uses **11.7** MB of virtual memory.

**trashapplet: **"You can drag items from Nautilus onto this applet to move them to your trash folder." -- Uses **19.2** MB of virtual memory.

**update-notifier: **"Puts an icon in the user's notification area when package updates are available." -- Uses **17.5** MB of virtual memory.

**wnck-applet: **"A library to use for writing pagers and task lists." -- Uses **19.0** MB of virtual memory.

I run Breezy on an old Thinkpad T20 with 256 MB of RAM and to me the above is **180** MB of not so well spent virtual memory (especially when I run Windows 2K on Qemu on top of all this). I'm not in every case sure whether or not these applets and daemons are safely removable, but I'll think I'll just try to see how much I can get rid of (while maintaining a useable desktop manager). Has any of you succesfully stripped Gnome of excess bloat? I'd like to hear. ;)

Of course I could switch to a more lightweight desktop/window manager, but I actually do like gnome, so I'm not saying goodbye to it without a fight. :razz:

---

### Post by tjwhaynes on 2005-10-19
[QUOTE=Azrael]In a fresh Breezy install and by *only* having the System Monitor open I see a sea of bloat. I'll list a few of the worst examples I see:

**clock-applet:** Uses **21.3** MB of virtual memory.
[/QUOTE]

Don't confuse Virtual Memory with Actual memory usage. It's not that simple. Each process can have a mix of shared and private memory usage. Looking at my system (AMD64), I see that the clock-applet shows 111.1Mb of Virtual memory, 11.8Mb of Resident memory and 8.5Mb of Shared memory. This breaks down as follows:
[LIST]
[*]Most of that Virtual memory is the Gnome Libraries. These are shared between all the Gnome components.
[*]The Resident memory is really the most important part - so the clock consumes 11Mb of memory map.
[*]Of that 11Mb, 8.5Mb is shared memory that is probably used by the underlying GNOME infrastructure and not specific to the clock-applet.
[*]That leaves about 2.5 Mb of memory that is private to the clock-applet.
[/LIST]

So while I could argue that 2.5Mb of memory for a clock applet is ridiculously high, it's not a big deal.

It's also worth pointing out that if you sum up the virtual memory consumption you will find that it far outstrips the physical AND virtual memory space you have available on your system. This is because you are counting the same library in memory multiple times. It's even more confusing than that because the Linux kernel provides a feature known as overcommit where a process may register the intent to use a certain amount of memory but it will not be physically allocated on the system unless it is needed. For example, firefox shows as taking up 255Mb of virtual memory on my AMD64 box but the process monitor shows that a TOTAL of 207MB is really being used by **everything running** on this system. 

Now on a 256Mb system, you probably do want to minimise the number of applets you are running. You may even wish to use a desktop like Xfce to reduce the amount of memory used still further, while still being able to use the Gnome apps. Don't run gdesklets for example. But my system is ticking along fairly nicely with a five tabs open in firefox and I'm not reaching that 256Mb limit.

Cheers,
Toby Haynes

---

### Post by Azrael on 2005-10-19
I knew virtual memory wasn't quite the same as the actual memory usage, but I wasn't aware of the extent of memory sharing and 'intent registering' you describe. Very informative post! Thanks.

---

### Post by denzilla on 2005-10-19
In my limited experience with Linux, I am somewhat shocked at how sluggish linux feels on older hardware. I got alot of older emachines lying around (300-450Mhz with 256meg RAM) with no MS Lic keys and I thought Ubuntu would run nicely on them. Needless to say, its like drag racing a Pinto! Its not just Linux as Open Office and Firefox run for crap on these PCs as well. What is it about Linux and OSS in general that makes them run like crap on legacy hardware? I could understand if they were 1st gen pentuims and EDO RAM equiped PCs, but this is madness. I can load Win2k and OfficeXP and they're very usable, but its also illegal ;)

---

### Post by Azrael on 2005-10-19
[quote=denzilla]What is it about Linux and OSS in general that makes them run like crap on leagacy hardware?[/quote] Linux itself doesn't run like crap on old hardware, much on the contrary even. If anything it's the desktop/window manager you use that is to 'blame'.

Try a window manager like IceWM, it will make a world of difference.

---

### Post by denzilla on 2005-10-19
Yea, I knew it was the desktop manager, but sheesh, gnome is so plain and the lighter managers like fluxbox just take it to a whole new level of plain. I just can't understand what is eating the cpu power up.

This isn't an Ubuntu bash, so please don't mistaken it for that. Just curious, thats all.

---

### Post by aysiu on 2005-10-19
XFCE is a good compromise--it's not plain jane and minimalistic, but it's not as sluggish as Gnome or KDE is on old hardware. Give it a shot!

---

### Post by denzilla on 2005-10-19
I tried XFCE shortly after Hoary got released. It was nice, but very glitchy on the machine I used at the time. Maybe its gotten better :)  I checked out IceWM and the themes for it looked decent, but changing managers always leads to issues with gnome/KDE apps not playing nice with it and I don't have the knowledge to fix the problems that arise. XFCE didn't seem to have a problem running other managers apps, though.

---

### Post by irusun on 2005-10-20
I think a lot of newbies get a little confused about running Linux on older hardware.  Just like Windows software, Gnome/KDE and related software have gotten much more sophisticated over the years. 

Gnome may seem really simple on the surface, but it takes a lot of resources to give the impression of simplicity and making sure things just work.  You can't expect the current version of OpenOffice to run any faster on old hardware than you would MS Office 2003.

If you want to use old hardware, you've got to use a lighter desktop with less thrills.  There isn't a magic trick that lets old hardware use all the advanced features of the latest software at the same speed as new hardware.

---

### Post by SickTwist on 2005-10-20
There are many things that can be disabled in GNOME to give better performance on older hardware.  I have used the following tricks with Ubuntu (running GNOME) on a PII 233 mHz 192 MB machine with decent results:
[LIST]
[*]use less resource intensive themes for metacity (Atlanta is good) and GTK+
[*]configuration editor: apps -> metacity -> general -> reduced_resources=true
[*]configuration editor: apps -> nautilus -> preferences -> show_desktop=false
[*]use only one panel with a minimum of applets
[*]disable background picture
[*]use only one workspace
[/LIST]
It's not as glorious to look at but it's still very functional.

---

### Post by doclivingston on 2005-10-20
On one side you have people saying Gnome is too bloated, on the other side you have people complaining that Gnome doesn't have the features they want - which means developers have a fine line to walk.

---

### Post by pigmelt on 2005-10-20
have you tried Ubuntulite yet [www.ubuntulite.org](www.ubuntulite.org) it is suposed to work well on older machines.

---

### Post by Miguel on 2005-10-20
Hi all,

Actually, I find that gnome and kde have lots of features. The fonts look cool. Cairo looks cool. The panels (mainly in gnome, I don't find kde all that attractive) are IMHO much better than windows'. Nautilus does lots of things. To tease my girlfriend, I once put my mouse over a mp3 and it started playing. Her jaws dropped. And she hasn't seen composite.

But I do find it quite slow (on a laptop with a 4ksomtehing rpm hd) to load and slow to redraw (fglrx doesn't precisely satisfy my soul). While most of this can be due to X11 (I am eager to test X11R7), it must be remembered that OSS is community driven. Do you really want to spend your (probably free) time looking at lines of code to achieve better memory management and lower mem and cpu usage? Please, think twice: you will get more fame developing alpha blending or FSAA or normal-mapped icons or whatsoever.

While optimization is important, it is a very ungrateful job. And as all this goes about freedom, we cannot force anyone into optimizing metacity (hell not even ATi opimizes its own fglrx drivers!!!).

Changing subject, iceWM does a good job. With a good theme and rox, it can surpass win98 or win2k GUI  (thanks to its configurability). But it is a bit rough, and is a bit tricky to configure, and the menu's are not the friendliest ever to edit (a gnome user shouldn't complain about this). 

Anyway, try to see vista working on a 2 year old machine (especially if it has an intel 855 integrated graphics card). Even with MS' resources, as doclivingston said, it is a thin line between bloat a features.

Sorry for this long rant,

Miguel

BTW: I don't need linux domination of the world. I just need that people respect my freedom and don't send me word attachments.

PS: I think I'm spending too much time in front of a terminal lately...

PS2: I'm feeling quite at home with XFce 4.2.2 as of lately

---

### Post by kakashi on 2005-11-02
i my experiance if you remoe all hese gnome applets then you might as well move to ive-wm. 
i did and it lightning fast now.
also every gnome and kde program i've installed runs well only i need to start it from the command line.

---

### Post by grizzly on 2005-11-05
For those thinking that gnome is slow coz of features, i will like to point them to a proggie "Powerpro", windows powerpro to be more precise.
Currently this app is taking 1.3mb's of memory and the functions it provide are literally limitless. Think of any feature and it would have it. 

mouse gesturs, macros, bars, menus(dock them, call them with keyboard, gestures), virtual desktop, keylogging, alarm, schedule, clipboard & file monitor, alt+tab with mouse wheel, and lots lots more. and i haevn't even touched scripting yet!!
I doubt this, but is there any app like this for linux??

It seems gnome is like badly done , IMHO - jsut look at powerpro and you will see the differnence

Trying linux has become pain thanks to Gnome, its sooo slow, PLease ppl (UBUNTU GODS) pity us mortals and get something better. Get something like powerpro, plzzzzz.
I would try those icewin and xcfe but then those compatibilty problems :cry:

---

