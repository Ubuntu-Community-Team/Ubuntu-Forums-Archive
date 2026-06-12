---
title: "ubuntu vs kubuntu"
date: 2007-03-06
forum: Desktop Environments
---

### Post by eidolonnights on 2007-03-06
First, let me begin by saying that I love Ubuntu.  The community, the support, everything.  I've tried tons of other distributions, and I keep coming back to (k)ubuntu.  About the only other distro I've found that even comes close is openSUSE.

PCLinuxOS and Mepis are great projects, but lack polish.  Fedora?  Don't even get me started.

Now, for my conflict.  Ubuntu is great, I love it, but I prefer KDE.  So I head over and grab Kubuntu.  Simple solution, right?  Apparently not.  Everywhere I go people say that Kubuntu is simply Ubuntu with KDE installed by default.  If so, why does Ubuntu flawlessly recognize a graphics card that Kubuntu struggles with?  Pardon me if I'm wrong, but I thought that the DE had little to do with the hardware.  So this leads me to belief that Ubuntu and Kubuntu are NOT the same, and that there are differences extending beyond that of the DE.

So, I guess my next option is the install Ubuntu and then add KDE.  Of course, then I'll have to get rid of all the gnome junk, and maybe deal with a slower system.  I suppose that I could also go back to SUSE, but that lizard is just so silly lookin...

---

### Post by akajonesy on 2007-03-06
have you tried installing kde desktop but then removing gnome through synaptic? Might install and remove all in one go. (I'm a linux newb so take that suggestion w/a grain of salt).

---

### Post by yaztromo on 2007-03-06
> **eidolonnights said:**
> If so, why does Ubuntu flawlessly recognize a graphics card that Kubuntu struggles with?

Could you elaborate?

---

### Post by FooAtari on 2007-03-06
I run Kubuntu for a couple of days. I too prefer the KDE desktop, but found it to be a bit unstable on my laptop.  After a bit of reading it would appear the Kbuntu is less stable than Ubuntu in general, maybe because it isn't given the primary focus?

Unfortunately I had problems with all other KDE distros I tried.  I really like the look of Freespire but couldn't get the live CD to boot.  Apparently there is a known issue with the hardware in this laptop...

---

### Post by miggols99 on 2007-03-07
I prefer KDE as well. One thing that happens to me sometimes is that programs sometimes just randomly close or sometimes I am just logged out.

---

### Post by true_friend on 2007-03-08
It creates problems some time.
 i noticed if there is some programs crashed you cannot run it again untill it is removed from processes. i use this command for it 
kdesu ksysguard with Alt F2(in run dialog) and then remove the program crashed then it starts normally.

---

### Post by ComplexNumber on 2007-03-08
[quote=eidolonnights] PCLinuxOS and Mepis are great projects, but lack polish.[/quote]
i would agree about mepis lacking polish (eg ugly and disorganised menus etc), but PCLinuxOS's is probably one of the most polished kde distros out there. that and suse. apart from the frequent crashes, i really liked PCLinuxOS when i used it. the default look'n'feel is second to none amongst kde distros.


[quote=eidolonnights]
If so, why does Ubuntu flawlessly recognize a graphics card that Kubuntu struggles with? Pardon me if I'm wrong, but I thought that the DE had little to do with the hardware.[/quote]
actually, i've noticed that gnome appears to be better at recognising hardware too. i say "appears" because its true that the hardware detection is more kernel level, but the difference may be in how the different desktops handle the job of 'recognising' or registering the detection. gnome seems to do a better job of it.

---

### Post by tagginannie on 2007-03-08
From What I've been reading Ubnutu never really supported KDE, it is
only a marketing tool for Gnome. I also notice that KDE has a lot more
bugs and crashes often on Ubnutu than with other distros that I have
been playing with lately (PCLinuxOS, Gentoo, Sabayon, Foresight) and 
it runs faster too

---

### Post by Paraparaumu on 2007-03-19
So far, I've got to agree with tagginannie. I tried Kubuntu (6.10), coming from Mandriva where KDE was always my preferred desktop. Things crash at random, especially the Adept installer. The "Focus Follows Mouse" setting that I always used on Mandriva (one of the reasons I like KDE) appears to confuse the system when I use my preferred Keramic window decoration style, so that focus cycles at max speed between different applications when I hold the mouse over a window that's in front of another window. That part I'm at least able to get around by changing to another decoration style.

Installing some software doesn't appear to install all necessary dependencies, too. I installed a GUI interface for ndiswrapper in a (so far vain) attempt to get my wireless working with Kubuntu (a whole separate adventure, involving the distribution knowingly including a broken ndiswrapper install, apparently so as to avoid breaking compatibility with upgrades). That created a nice menu entry, which does precisely nothing when I select it. It turns out the menu expects to use "gksudo", which is not installed on my system and which I so far haven't tracked down. Presumably it's part of Gnome that the packagers expected to have available automatically.

I'm starting to think that (K)Ubuntu is a good distribution for people coming from Windows and new to Linux, but not really designed for those who've been using Linux for some time and know what they want. Too bad - I was hoping it'd live up to the reviews I've read.

---

### Post by errhec on 2007-03-19
Hi
the comand " gksudo " is the comand not the application and is ROOT !!!!!
if you use it in terminal like "gksudo nautilus" it will turn up the window where you can do the same things like in  explorer ( rename , delete... ) but you can destroy the OS !!! 
So U must know what you are doing.
Try to run application with gksudo comand from terminal.
BY
Hope it helps

BTW 
I run on Kubuntu 7.04 and is PERFECT :) , all HW was detected and did not have any problems
with normal work.
errhec

---

### Post by turningt on 2007-03-19
What is the nature of the issue, is the x-server not loading the correct driver in one installation over the other, or are you experiencing performance issues where the correct driver is loaded but not working correctly? Could you post the configuration file please? Both these distros use the same x-server setup supposedly, so.... 
i run edgy kubuntu, have since it came out, basically i had to learn to use kdesu instead of the gnome graphical sudo command, (sorry cant remember it right now, im on windows due to being on break at work). The sound system was a little getting used to with Artsd instead of esd, and frankly i could not live with the control panel as it was, so i went back to the KDE official control center. 
     Yes, I have had to tweak a bit, but the installation is quite comfortable. I have found that most if not all of the fixes i have needed i can find in the regular Ubuntu Forums, though i still check the Kubuntu forums as well, and of course i did migrate from Debian sid, so my comfort level may just be in comparison... 
Sorry for the novel, here is a link if you prefer to move to a more basic KDE installation... [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by Linux_oid on 2007-03-31
I've just installed kubuntu 6.10 on old (Pentium III, 500M) box. This was the only distro   which could be easy installed (30 min something). Niether ubuntu, nor xbuntu wanted to be installed (was frozen in a process). 

Ono more distro I'd mension is VectorLinux 5.8 SOHO (KDE as well). However  moving from ubuntu to slack is hard. 

One thing I noticed was wireless net support. I'm having problem when I restart box. When I have another box online, kubuntu gets confused and doesn't go online automatically.

---

