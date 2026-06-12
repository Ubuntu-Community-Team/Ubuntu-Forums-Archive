---
title: "Is it me or is Ubuntu very very slow?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by kieranjones on 2006-06-06
Hi,

I've recently installed the latest version of Ubuntu onto my laptop, and I can't help but notice that it's very very slow, particularly with programs like Firefox which takes 8 seconds to load, compared with the 3 it takes in Windows XP, Evolution isn't much better, taking about 9 seconds and don't even get me started on any programs more complicated.

Is there any solution to this?

I had a look at running processes to see if there was something eating away at RAM and I tell you what, why is the clock applet using 8mb of memory? There are a lot of mystical looking programs using large amounts of a fairly limited resource on the laptop. It's only got 256mb of RAM to start with.

Any help to speed this thing up would be greatly appreciated, as I really don't want to be forced to go back to the currently faster Windows XP.

---

### Post by padre999 on 2006-06-06
There is a little howto on this subject...

[http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)

---

### Post by kieranjones on 2006-06-06
Thank you, I hadn't seen that topic. I'll look into it and hopefully it will solve my problems :)

---

### Post by padre999 on 2006-06-06
you are welcome

there are also some threads on configuring ubuntu for low specs computers. you might also find those helpful.

---

### Post by sdamron on 2006-06-07
It is you :o)  Kidding!  I thought I would document my system specs for those who are having troubles...Just FYI.

AMD Sempron 1.6ghz
1.5 gig ram (3300)
120 gig Samsung HDD
DVD Burner (It actaully works)
CD Bruner (It works too)
NVIDIA FX 5500
Micro$oft USB Wireless Mouse (WOW!!  IT works too)
USB Keyboard (Can't remember brand) (Works inside Ubuntu, but not to choose OS at GRUB)
100 Gig Maxtor HDD
Firewire Card (Purchased from Fry's Electronics for 12 Dollars US)
17" LCD (No DMI) (Purchased from Amazon.com for 149 US Dollars)

I just wanted a good utility PC, not really a huge gamer or anything, I do play GuildWars from Windows on my IBM Laptop, but that is it.  Everything with the exception of my USB keyboard works as expected.  I may try this again when I am in front of my PC, so I can give specifics on DVD/CD/Keyboard.

---

### Post by geller6980 on 2006-06-11
I have a similar system... did you ever get this problem restored?

---

### Post by missmoondog on 2006-06-11
i have 3 systems with lower specs than yours that don't take that long to load those items you mentioned, and that's without any tweaking. have tweaked all boxes by just using bum. dapper drake runs almost as fast as xp pro USED to on these same systems. i say USED too because i no longer have winblows installed on these systems, or the other 2 boxes i have, with better specs than yours.

---

### Post by 3rdalbum on 2006-06-11
The different memory indicators are always misleading.

For instance, with the clock applet on my system right now:
38.3 MiB Virtual Memory
9.6 MiB Resident Memory
7.5 MiB Shared Memory

The first two instances of Apache on my computer are using 223 MiB of Virtual Memory each, but only 1.7 Resident and 1.1 Shared. How on earth can a sleeping web server be using up almost twice my system memory? Answer: It's not. It's probably not even using the 1.1 MiB.

---

### Post by RawMustard on 2006-06-11
It's not you, linux desktops are much slower than windows ones.  It's the price you pay for freedom.  But remember, as windows ages it will get slower and slower, but linux will stay the same slow speed until you update it in years to come with a faster version.

---

### Post by MKR. on 2006-06-11
[QUOTE=RawMustard]It's not you, linux desktops are much slower than windows ones.  It's the price you pay for freedom.  But remember, as windows ages it will get slower and slower, but linux will stay the same slow speed until you update it in years to come with a faster version.[/QUOTE]

Really? My Ubuntu install is much faster than my XP install, and handles higher loads without stuttering (and my XP install runs as fast as it did when I installed it back in 2003).

---

### Post by tronica on 2006-06-11
I've never have had any slow downs with ubuntu,  or any distro for that matter.

---

### Post by RawMustard on 2006-06-11
Yes yes, I've heard it all before and don't be offended if I don't believe you.
Linux desktops are not faster than XP and that's a fact - Video drivers for linux are not as fast as windows ones and xorg is nowhere near being as fast as windows and neither is gnome or kde.  When it comes to heavy hauling in the background, then yes linux is better, but most average users will not see this, all they see is the lack of responsiveness from their desktop environment;  things like windows trailing, slow menus, jerky video performance, apps taking far too long to load etc, etc!

As for a 3 year install of XP, either you don't use it much or have not noticed the slowdown, install it fresh and then say it's the same as it was before!

---

### Post by nlife on 2006-06-11
First of all, you have to convince yourself that slower is better and that in three years XP will be slower than uBuntu is now :lol: Just keep telling yourself that slower is better... slower is better... :^o  :rolleyes: 

The other thing you can do is check the processor speeds. I found that on my laptop uBuntu was scaling the CPU back to 530MHz and would rarely hit the full 1.79GHz. Windows would be redrawn, mp3s studder, and everything in general ran slow. Run the following command in a terminal and add the applet to your taskbar.

$ sudo dpkg-reconfigure gnome-applets

Choose &#8216;Yes&#8217; to set the SUID bit for the cpufreq-selector executable and you&#8217;ll be able to left-click on the applet and set the the CPU frequency manually. Then you can choose the speeds you want your CPU to run at. When plugged in, I run at the full 1.79GHz, on battery I scale things back. I'm still having problems getting video to play on the web, mp3's pause when I move window, but slower is better. Not being able to watch video is better... ;-) 

N

---

### Post by leech on 2006-06-11
[QUOTE=RawMustard]Yes yes, I've heard it all before and don't be offended if I don't believe you.
Linux desktops are not faster than XP and that's a fact - Video drivers for linux are not as fast as windows ones and xorg is nowhere near being as fast as windows and neither is gnome or kde.  When it comes to heavy hauling in the background, then yes linux is better, but most average users will not see this, all they see is the lack of responsiveness from their desktop environment;  things like windows trailing, slow menus, jerky video performance, apps taking far too long to load etc, etc!

As for a 3 year install of XP, either you don't use it much or have not noticed the slowdown, install it fresh and then say it's the same as it was before![/QUOTE]

Not that I'm offended by what YOU said, but it is not a FACT that XP drivers are faster than Linux drivers.  Consider this, if you have a nVidia card, the driver is essentially the SAME as it is on Windows.  

Also, I have installed Ubuntu Dapper Drake on a friend's computer, along side Windows XP.  It is a 2.7ghz Celeron with 128mb of PC-133 ram (long story on that one, who knew that they made a socket 478 motherboard that supported PC-133 SDRAM....)  Ubuntu flies on the machine.  XP is slower than a sloth on it.  RAM is everything with XP.  If you don't have at least 256mb of RAM then it will simply crawl.  This is a freshly installed XP with SP2 and Avast Anti-Virus and Kerio Firewall.  That's it.  It literally takes about 5 minutes to even become usable.

Ubuntu isn't slow, at least in my experience.  A fresh install of it compared to a fresh install of Windows is not only slower on this machine, but it's also a lot less useful.  I even tested out load speeds and usage of OpenOffice on this computer.  Linux kicked it's butt.  

I have seen the same sort of redraws on the windows when you move them fast around in Gnome, KDE and Windows.  Even XGL has the tearing.  A lot of it is due to the theme you are using.

Leech

---

### Post by nalmeth on 2006-06-11
The difference is that you can strip your Ubuntu down to using fluxbox, or a little heaver for lightweight xfce. Prelinking apps makes them open faster, and you can reduce your boot-time drastically.

For OP, I would recommend xubuntu.

---

### Post by PsychoTrauma on 2006-06-11
[QUOTE=RawMustard]Yes yes, I've heard it all before and don't be offended if I don't believe you.
Linux desktops are not faster than XP and that's a fact - Video drivers for linux are not as fast as windows ones and xorg is nowhere near being as fast as windows and neither is gnome or kde.  When it comes to heavy hauling in the background, then yes linux is better, but most average users will not see this, all they see is the lack of responsiveness from their desktop environment;  things like windows trailing, slow menus, jerky video performance, apps taking far too long to load etc, etc!

As for a 3 year install of XP, either you don't use it much or have not noticed the slowdown, install it fresh and then say it's the same as it was before![/QUOTE]

And where are you getting these facts from? From personal experience gnu/linux is just as fast as xp home/pro if not faster in some instances. My desktop is very responsive and after opening firefox once (takes 2-3 seconds) it opens instantly the next time. My windows xp pro box stays the same speed as well since I keep it defragged and the registry clean. In fact to make my xp box as fast as the default ubuntu install I have to turn off a bunch of services.

amd64 2800+
asus k8v-se deluxe
2x 1 gig crucial ballistix mem 2-2-2-6
nvidia mx4000 (upgraded soon)

---

### Post by mumushi on 2006-06-11
This is my pc's specs

```
Pentium 2 233Mhz
asus board
128Mb PC100 SDRAM
S3 Trio 4MB
```

My Dapper drake runs faster than XP does :D

---

### Post by mumushi on 2006-06-11
actually i can't even install xp :D

---

### Post by trash on 2006-06-11
At first i dist-upgraded Breezy running xfce on top of gnome to Dapper and I was impressed with it's peppiness and overall speed, sadly during the last week of Dapper testing I did a routine upgrade and fried that install.

On the same machine(P3 450mhz 385ram),  I installed Xubuntu and it was slowe! I have now installed prelink, preload and 2.6.15-23-686 kenel which has improved things.

Xorg was also a bit of a problem running at 20% cpu all the time while bittornado was running and after an hour or so my system would stop responding, requiring a reboot. Kernel may have fixed that but I now use Azureus and Xorg is a respectable 1-5%

---

### Post by Adramelech on 2006-06-11
My ubuntu dapper starts like 5 times faster than my xp and I play enemy territory faster on ubuntu than on XP,  34 fps on windows, 75 on linux, only bad thing is my mouse lags.

Proc 2.8Ghz
Nvidia GeForce 4800

---

### Post by MKR. on 2006-06-12
[QUOTE=RawMustard]Yes yes, I've heard it all before and don't be offended if I don't believe you.
Linux desktops are not faster than XP and that's a fact - Video drivers for linux are not as fast as windows ones and xorg is nowhere near being as fast as windows and neither is gnome or kde.  When it comes to heavy hauling in the background, then yes linux is better, but most average users will not see this, all they see is the lack of responsiveness from their desktop environment;  things like windows trailing, slow menus, jerky video performance, apps taking far too long to load etc, etc!

As for a 3 year install of XP, either you don't use it much or have not noticed the slowdown, install it fresh and then say it's the same as it was before![/QUOTE]

Nope, gnome is quite zippy, whereas XP loads programs and draws windows as fast as it did back in 2003 (which is slow, and yes I did do some benchmarking [recording app load times] when I installed it so I would be able to compare down the road).

Personal experience != fact (usualy). Just because your system(s) handle XP better than Linux doesn't mean everyone else has the same experience.

---

### Post by mumushi on 2006-06-13
yup your right! I totally agree :)

---

