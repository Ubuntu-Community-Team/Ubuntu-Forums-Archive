---
title: "Gnome: Full screen Flash videos"
date: 2014-05-22
forum: Desktop Environments
---

### Post by tom94 on 2014-05-22
I've installed ubuntu gnome, hoping i were going to find a more rich de.
I was using xfce (xubuntu), and i really hoped that by the years i were going to find something remotely usable.
I told myself: "you are not pretending to do weird stuff with your os, atleast none that your music hardware isn't already allowing you to. ANY de is ok for watching videos, surf the web, managing usb's and hd's."

Gnome is really pretty, indeed.
At first i really thought that shell extensions were working around problems.
Then i went into this really worrying problem: can't fullscreen flash videos on the net. I've searched for many solutions only to discover there weren't any. There were only workardounds through devilspie that i couldn't make it work anyway. ANY of you know a solution for this problem NOT involving spending half an hour solving it?

I got so many little problems going on since the instlalation.
But this is the one. 
If i can't find a solution for this BASIC problem that allows me to solve it in a click, i salute you. I'm done. You are not defensible, GNOME 3, and you probably suck. Sorry for the devs, but this is what i think.

---

### Post by kurt18947 on 2014-05-22
I would tend so suspect a video problem.  I have a 2008ish Athlon II X2 desktop machine with an Nvidia 210 card.  I think the video card has 1 GB RAM.  I just opened and played a Youtube video full screen with no problem.  I am using Nvidia's driver, not the open driver.  What video card or system do you have?  One problem I've run into in the past is using onboard video and not allocating enough system RAM to the video system.  I would guess playing full screen video would require at least 256 MB. RAM, maybe 512.  I'm just guessing here but I doubt it's a Gnome issue.  Flash is a pig when it comes to processor usage so that could be an issue as well.

P.S. I'm running Ubuntu-Gnome 14.04

---

### Post by tom94 on 2014-05-23
youtube is most likely running html5 for you. The problem is note, but there's no one addressing it. Look here:

[https://bugzilla.redhat.com/show_bug.cgi?id=9ubuntu fullscreen81767]("https://bugzilla.redhat.com/show_bug.cgi?id=981767")
[http://forums.debian.net/viewtopic.php?f=6&t=109131](http://forums.debian.net/viewtopic.php?f=6&t=109131)
[https://bugzilla.gnome.org/show_bug.cgi?id=712622](https://bugzilla.gnome.org/show_bug.cgi?id=712622)
[https://bugzilla.gnome.org/show_bug.cgi?id=700288](https://bugzilla.gnome.org/show_bug.cgi?id=700288)
[https://bugzilla.gnome.org/show_bug.cgi?id=705177](https://bugzilla.gnome.org/show_bug.cgi?id=705177)
[https://bugzilla.gnome.org/show_bug.cgi?id=643740](https://bugzilla.gnome.org/show_bug.cgi?id=643740)


If you could try to open a video on, i don't know, Vimeo, Nowvideo, or sorts... See if you happen to have same problem...


There are a lot of people with this specific problem, and many saying this is unsolved since gnome 3.4.

 YEARS without a solution, basically because developers don't see this as a problem, since it regards the shell behaviour.

They are arguing about philosophical matters. Nobody is willing to take this issue as important. I'm clearly not the user GNOME is made for...

By the way, i've installed kubuntu desktop right now on the same system, and videos are working properly. On the same pc, i've tried before shifting to ubuntu gnome: xubuntu, kubuntu, mint (cinnamon). None of these systems got this problem, so is not a vga or hardware problem. It appears to be related also to flash-player, which works correctly on every other de's...

The thing that's worrying in my opinion is that this thing is not being issued as important... I can't hold myself from thinking: every time i see things like this, i think that somewhere, around the world, GNU\LINUX is loosing some new users... It's a pity.

---

### Post by kansasnoob on 2014-05-23
GNU\LINUX consists of more than just GNOME :)

I'm using Ubuntu Trusty + [Flashback w/Metacity]("http://ubuntuforums.org/showthread.php?t=2220264") to stream full-screen flash from Hulu, CWTV, and other sites with no problems on this hardware:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Works nearly as well on this hardware:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM


---

### Post by tom94 on 2014-05-23
my hardware is as follow.
AMD fx 8350 
Sabertooth 990fx
ATI HD 7870
8 GB DDR3 RAM

Well, anyway i'm most surely going back to xubuntu, or i'll try again kubuntu, maybe playing at tweaking it a little...
As for now, kde and xfce remain the most stable de i've tried recently...

I'm still hoping someone found an alternate (working) and easy solution to the mentioned problem :(

---

### Post by kurt18947 on 2014-05-25
I wonder if this has to do with ATI/AMD hardware.  I looked through some, not all the bug reports.  Most do not mention hardware in use.  I only saw one report where hardware was mentioned and that reporter had ATI/AMD video as well.  I just tried a site that is definitely using flash (thewoodwhsiperer.com)and it opens full screen no problem on a Thinkpad with Intel 945(?)chipset.  I'll try a couple different machines tomorrow.

It's tomorrow:).  I've tried the above web site on two additional machines.  The first is an GigaByte AMD MoBo w/Nvidia 210 graphics.  The second is a new Asrock board with A6-6400K AMD APU using built-in graphics.  All three run full screen flash with no apparent issues.  Obviously there **are** issues but I'm not seeing them on my machines. Some ATI/AMD graphics had a rep for not playing well with linux.  Have you tried disabling hardware acceleration?  I don't know if that would help but it's pretty easy to do and to reverse.

---

