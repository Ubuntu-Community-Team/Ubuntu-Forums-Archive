---
title: "HELP:  Seeking Guidance on Linux: Gaming Machine."
date: 2010-01-17
forum: Gaming &amp; Leisure
---

### Post by Panties on 2010-01-17
Hi Ubuntu users and Ubuntu Gurus,

I was playing my Xbox360 the other day, and I just came up with an Idea.

Well, to begin with, console gaming are custom made for gaming, lets take one, for example:-

[http://support.xbox.com/support/en/us/xbox360/hardware/specifications/consolespecifications.aspx](http://support.xbox.com/support/en/us/xbox360/hardware/specifications/consolespecifications.aspx)

The hardware and the specifications was dedicated, for games only! Throw in almost every XBOX DVD games, it run gracefully & MAX IT OUT LOUD TOO!


Okay, so here is my idea. (Thus, I am only playing World Of Warcraft most of my time)

I am going to build a new gaming machine. But, In that gaming machine, say "Good-Bye" to windows XP,Vista,7...etc... (I heard Windows 7 was fast, but I want it FASTER..)

I'm not worried about HARDWARE, (I go for NVIDIA, best for linux), it is the OS/sofware that I am worried the most!

ONLY PURE WORLD OF WARCRAFT! No mozilla, no background desktop(if possible), no services.... pure empty...  Just Linux Kernel and the Game itself.

[U][B]My CONCERN IS:-

[/B][/U]1. I did my research, and it came to me that I might choose either Ubuntu Desktop, Ubuntu Server or Gentoo...
Why?
Ubuntu Desktop:- Its running linux, but there are some memory usage as well, like updates, other software, there are some services running in the background like Ubuntu Updates.... mozilla... SELINUX... which I plan to stripped/remove it away.... pure naked!
 Only Graphic Card, SoundCard, Network card, is all that is required to play WOW...

Ubuntu Server: Its running linux and Uncheck all the LAMP,Mail.. etc, and strip/remove SELINUX.... Just pure Naked! 
  Only Graphic Card, SoundCard, Network card, is all that is required to play WOW...

Gentoo: Another Linux, build your own linux, lay down the necessary foundation (Graphic Card, SoundCard, Network card) just for World of warcraft..


and put World Of Warcraft into Startup, so that when I turn on my machine, it launch the game! thats all I want!  _***Dedicated all Hardware Resources, every juice of it, to World Of Warcraft!***_


Remember, just Kernel, and the game..

2. Which should I choose? Crossover? Wine? or Cedega? for WOW! (I am not planning to install any other games, just WOW) Which offers the Best Graphic?

3. READYBOOST for Windows Vista/Windows7, is there any "READYTUX" for Linux?  (LOLX), I plan to dedicate a pendrive, to use for my LINUX...

4. Input devices: Mouse and Keyboard, perhaps G15 Logitech Keyboard... 

5. There is no need for Anti-virus, Firewall, Any form of Security, D.E.P. by windows, Plug & Play running in the backgound whenever you plug in your pendrive, Themes, AERO, IM-Messaging like MSN/YAHOO, etc.. etc.. etc... What else? 
I think that's about it! It wont be too difficult to ask, right?

6. Should I choose 32 bit Linux? (Coz most games, if OS is running 64bit, the games will run emulatedly through 64bit. In another words, they emulate 32bit enviroments, please correct me if im wrong..)

Yeah, thats all I want... a World Of Warcraft Console Gaming on the PC..


I plan to get the PC hardware by this week... an ICore7 Motherboard. Please let me know your comments. Also, What Nvidia Card work best, in linux enviroment! 

Thank You! :D

---

### Post by tommcd on 2010-01-17
> **Panties said:**
> 

Ubuntu Server: Its running linux and Uncheck all the LAMP,Mail.. etc, and strip/remove SELINUX.... Just pure Naked! 
  Only Graphic Card, SoundCard, Network card, is all that is required to play WOW...
Remember, just Kernel, and the game..

You will still need to install the X server and a desktop environment, or at least a window manager like Fluxbox or Window Maker, in order to install the nvidia driver and run a graphical game like WOW.
I understand your idea though.  A system without a lot of bloat will free up resources for the game.
You might consider Arch linux. With Arch you install a bare bones command line system, then you install just the packages you want. In this way you get a customized system that suits your needs. Arch is much easier and faster to install than Gentoo. Arch is also very fast and  up to date. Arch always uses the latest kernel and packages.
Read their beginners guide for how to install:
[http://wiki.archlinux.org/index.php/Beginners'_Guide](http://wiki.archlinux.org/index.php/Beginners'_Guide)
And read about the "Arch way":
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)
You could also do a minimal install of Ubuntu, then just get xorg and gnome or xfce or whatever:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I don't play WOW, so I can't advise on whether to use Wine, Crossover, or Cedega.

---

### Post by konqueror7 on 2010-01-17
so, its a bootable WoW? :D

you can try Remastersys after installing and configuring your 'distro', so can share it...:D

---

### Post by Panties on 2010-01-17
> **tommcd said:**
> You will still need to install the X server and a desktop environment, or at least a window manager like Fluxbox or Window Maker, in order to install the nvidia driver and run a graphical game like WOW.
I understand your idea though.  A system without a lot of bloat will free up resources for the game.
You might consider Arch linux. With Arch you install a bare bones command line system, then you install just the packages you want. In this way you get a customized system that suits your needs. Arch is much easier and faster to install than Gentoo. Arch is also very fast and  up to date. Arch always uses the latest kernel and packages.
Read their beginners guide for how to install:
[http://wiki.archlinux.org/index.php/Beginners'_Guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide")
And read about the "Arch way":
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)
You could also do a minimal install of Ubuntu, then just get xorg and gnome or xfce or whatever:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I don't play WOW, so I can't advise on whether to use Wine, Crossover, or Cedega.

[COLOR=SeaGreen]X server and a desktop environment, or at least a window manager like Fluxbox or Window Maker, in order to install the nvidia driver and run a graphical game like WOW.


[COLOR=Black]ArchLinux over Gentoo? U ure ArchLinux is better anytime? & hmm.. a GUI window for linux. That is another qood question. Which Window Manager of linux, would give me the BEST 3D? Any recommendation? I dont want any fancy Gadget Enhancement desktop... just a GUI Desktop that work BEST for OpenGL/D3D! What do you think?[/COLOR]
[/COLOR]

---

### Post by Panties on 2010-01-17
> **konqueror7 said:**
> so, its a bootable WoW? :D

you can try Remastersys after installing and configuring your 'distro', so can share it...:D


Yeap! A bootable WOW! =)
Sorry for my "noobness", but.. what do u mean by... "[COLOR=DarkGreen]REMASTERSYS[/COLOR]" ?

---

### Post by DarthScape on 2010-01-18
You might be able to set the flash drive as the swap partition, thats basically what windows does, copies the virtual memory to the flash drive.

---

### Post by konqueror7 on 2010-01-18
> **Panties said:**
> Yeap! A bootable WOW! =)
Sorry for my "noobness", but.. what do u mean by... "[COLOR=DarkGreen]REMASTERSYS[/COLOR]" ?

oh, forgot the [link]("http://www.geekconnection.org/remastersys/remastersystool.html")...remastersys allows you to backup your current system into a livecd or iso. so you can later distribute it or install it again without doing all of it again...

---

### Post by tommcd on 2010-01-18
> **Panties said:**
> [COLOR=SeaGreen]
ArchLinux over Gentoo? U ure ArchLinux is better anytime?
I have never used Gentoo, so I can't say if Arch is better than Gentoo.
If you want a customized system that is light, fast, and up to date, then Arch is very hard to beat.
The only advantage I can see with Gentoo is that, since it is a source based system, you can really go hard core and compile each and every package (kernel, xorg, etc) with your specific customizations. Keep in mind that this is very time consuming though. Gentoo takes quite a while to install from what I have read.
 Arch has something similar called the Arch Build System that would allow you to accomplish essentially the same thing with Arch though:
[http://wiki.archlinux.org/index.php/Arch_Build_System](http://wiki.archlinux.org/index.php/Arch_Build_System)
I never used the ABS when I was running Arch though. I just used the binary packages straight from the Arch repos, which worked fine for me. 
> **Panties said:**
> 
 Which Window Manager of linux, would give me the BEST 3D? Any recommendation? I dont want any fancy Gadget Enhancement desktop... just a GUI Desktop that work BEST for OpenGL/D3D! What do you think?

I don't think one window manager would have any advantage over another when it comes to 3D performance. The possible advantage to using Fluxbox or Window Maker over a desktop environment like KDE or Gnome, is that the window managers use fewer computer resources, so more of your CPU, memory, and video card would be available for gaming. On a modern fast gaming rig though I would think the performance increase from using a window manager over a desktop environment would be small.
If you want convenience, go with XFCE, which is a desktop environment, but a simple and no-frills one compared to Gnome or KDE. 
If you really want bare bones, then try Fluxbox. I have used Fluxbox (a little bit anyway) in Slackware and it is easy enough to learn. A lot of Slackers also like Window Maker, but I have not tried that.

---

### Post by Panties on 2010-01-18
> **DarthScape said:**
> You might be able to set the flash drive as the swap partition, thats basically what windows does, copies the virtual memory to the flash drive.
 
 
So, putting those swap into the pendrive, is faster? or Put it in the Harddrive? 
Izzit safe? becoz linux wasn't design to take advantage of pendrive being stored as swap, right? Would it be "fast"?

---

### Post by Panties on 2010-01-18
> **konqueror7 said:**
> oh, forgot the [link]("http://www.geekconnection.org/remastersys/remastersystool.html")...remastersys allows you to backup your current system into a livecd or iso. so you can later distribute it or install it again without doing all of it again...
 
Oh... but only for Debian? is there a backup utility for windows? so that if windows corrupt, we can restore it from CD instead?

It will be troublesome if we have to reinstall windows, enter CDkey, apply Drivers.. lolx.. time consuming...... what about.. just.... Backup in the DVD, then reboot, it will install everything automatically?

---

### Post by Panties on 2010-01-18
> **tommcd said:**
> I have never used Gentoo, so I can't say if Arch is better than Gentoo.
If you want a customized system that is light, fast, and up to date, then Arch is very hard to beat.
The only advantage I can see with Gentoo is that, since it is a source based system, you can really go hard core and compile each and every package (kernel, xorg, etc) with your specific customizations. Keep in mind that this is very time consuming though. Gentoo takes quite a while to install from what I have read.
Arch has something similar called the Arch Build System that would allow you to accomplish essentially the same thing with Arch though:
[http://wiki.archlinux.org/index.php/Arch_Build_System](http://wiki.archlinux.org/index.php/Arch_Build_System)
I never used the ABS when I was running Arch though. I just used the binary packages straight from the Arch repos, which worked fine for me. 
 
I don't think one window manager would have any advantage over another when it comes to 3D performance. The possible advantage to using Fluxbox or Window Maker over a desktop environment like KDE or Gnome, is that the window managers use fewer computer resources, so more of your CPU, memory, and video card would be available for gaming. On a modern fast gaming rig though I would think the performance increase from using a window manager over a desktop environment would be small.
If you want convenience, go with XFCE, which is a desktop environment, but a simple and no-frills one compared to Gnome or KDE. 
If you really want bare bones, then try Fluxbox. I have used Fluxbox (a little bit anyway) in Slackware and it is easy enough to learn. A lot of Slackers also like Window Maker, but I have not tried that.
 
 
Yeah.. its true..! Since it is a gaming rig, and everything is at HIGH spec...? Therefore, it wont be noticable though... However, I go ahead with Fluxbox then, just wanna use fewer computer resources.. :D

Should I go for Pentium or AMD? which one that Linux work best on?

---

### Post by Grenage on 2010-01-18
If you're building a machine for just one game, wouldn't it be wiser to use that game's native OS?

---

### Post by tommcd on 2010-01-18
> **Panties said:**
> 
Should I go for Pentium or AMD? which one that Linux work best on?
The Intel core 2 duos and newer core i7 CPUs are supposed to offer much better performance than the AMD Phenom CPUs. The Intel chipsets tend to work well on linux also. For a high performance gaming rig I would think Intel would be the way to go.
The late model Intel CPUs are more expensive than the AMD CPUs though.

---

### Post by tommcd on 2010-01-18
> **Grenage said:**
> If you're building a machine for just one game, wouldn't it be wiser to use that game's native OS?
This is a good point; and one that should not be overlooked. It may well be that Windows XP would offer better performance in WOW than any linux distro simply because the game was made to run on Windows systems.
Perhaps Panties could dual boot with XP and compare the performance between Windows and linux. Windows XP can be tweaked to improve it's performance by disabling all of the many non-essential services that are running on a default install of XP.

---

### Post by konqueror7 on 2010-01-18
> **tommcd said:**
> The Intel core 2 duos and newer core i7 CPUs are supposed to offer much better performance than the AMD Phenom CPUs. The Intel chipsets tend to work well on linux also. For a high performance gaming rig I would think Intel would be the way to go.
The late model Intel CPUs are more expensive than the AMD CPUs though.

i don't know the exact performance gap, but there is news that intel made amd-based system run code slower...

[http://www.downloadsquad.com/2010/01/04/intel-forced-to-provide-a-compiler-that-isnt-crippled-for-amd-processors/]("http://www.downloadsquad.com/2010/01/04/intel-forced-to-provide-a-compiler-that-isnt-crippled-for-amd-processors/")

---

### Post by Panties on 2010-01-18
> **Grenage said:**
> If you're building a machine for just one game, wouldn't it be wiser to use that game's native OS?
 
Wiser? Microsoft (or MAC)?

Nope. I always eager to learn Linux, but I blame most of the game developers (like blizzard), who only makes game for MAC or Windows...

I only like WOW, would it be better to port it to run under linux?

I was always amazed by Console. Graphics&Gameplay in Console, always turn out to be better than most PC. I understand that their games are optimized to run on that Console.

My project "Gaming" machine, would just be a start. I bet that if we could stripped down all the services from windows, it will generally boost the game itself.

Furthermore, I think Microsoft should Come out with... "Ms. Windows (Gaming Edition)", it should hit the market.

Anyway, that's beside the point. Why not try linux? We get to learn something too! =)

---

### Post by Grenage on 2010-01-18
Because WoW will likely be faster and more stable on a windows install, isn't that what you ultimately want?

---

### Post by Panties on 2010-01-18
> **tommcd said:**
> The Intel core 2 duos and newer core i7 CPUs are supposed to offer much better performance than the AMD Phenom CPUs. The Intel chipsets tend to work well on linux also. For a high performance gaming rig I would think Intel would be the way to go.
The late model Intel CPUs are more expensive than the AMD CPUs though.
 
Okay.. Which model of NVIDIA that linux support? Will it kick in, if I buy the Latest NVIDIA card, but the linux driver are not out yet?

---

### Post by Panties on 2010-01-18
> **Grenage said:**
> Because WoW will likely be faster and more stable on a windows install, isn't that what you ultimately want?
 

I want Faster & stability... But  I do want to be able to control my computer process...

I want full control, I believe linux deliver that!

---

### Post by Panties on 2010-01-18
> **tommcd said:**
> This is a good point; and one that should not be overlooked. It may well be that Windows XP would offer better performance in WOW than any linux distro simply because the game was made to run on Windows systems.
Perhaps Panties could dual boot with XP and compare the performance between Windows and linux. Windows XP can be tweaked to improve it's performance by disabling all of the many non-essential services that are running on a default install of XP.
 
 
Dual... so that means, I need to Dual-Boot, ... I need to buy 2 Harddisk, right? :)

---

### Post by tommcd on 2010-01-18
> **Panties said:**
> Okay.. Which model of NVIDIA that linux support? Will it kick in, if I buy the Latest NVIDIA card, but the linux driver are not out yet?
I would think that the nvidia 9000 series or the GTX 200 series cards would offer the best performance. According to the nvidia web site the GTX 200 series is supported with the latest 190 drivers:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

---

### Post by Panties on 2010-01-18
> **Panties said:**
> I want Faster & stability... But I do want to be able to control my computer process...
 
I want full control, I believe linux deliver that!
 
 
To answer your question, My goal is to turn a PC, into a gaming console, since there are no OS that does that.... (OS which dedicate for gaming only!)

---

### Post by Panties on 2010-01-18
> **tommcd said:**
> I would think that the nvidia 9000 series or the GTX 200 series cards would offer the best performance. According to the nvidia web site the GTX 200 series is supported with the latest 190 drivers:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)
 
 
GTX 200.... ok, whic model of Intel chipset would be good?

---

### Post by tommcd on 2010-01-19
> **Panties said:**
> GTX 200.... ok, whic model of Intel chipset would be good?
Well, since you said in your first post that you wanted a core i7 CPU you will need one of the chipsets that support it. Phoronix has done some reviews of the P55 chipset and the X58 chipset using core i7 CPUs on Ubuntu:
[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1)
I think the X58 chipset is more performance oriented than the P55. Motherboards with the X58 chipset may be more expensive though.
For specific motherboard recommendations and the like, you can try asking on the Phoronix forums. You will likely find people there with experience running core i7 in linux.

---

### Post by Panties on 2010-01-19
> **tommcd said:**
> Well, since you said in your first post that you wanted a core i7 CPU you will need one of the chipsets that support it. Phoronix has done some reviews of the P55 chipset and the X58 chipset using core i7 CPUs on Ubuntu:
[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1)
I think the X58 chipset is more performance oriented than the P55. Motherboards with the X58 chipset may be more expensive though.
For specific motherboard recommendations and the like, you can try asking on the Phoronix forums. You will likely find people there with experience running core i7 in linux.


Thanks for the information. I'm heading to that website now. I am also considuring the DELL XPS 1800 Desktop. I have to scout around before I make my final decision. I'll keep you posted.

---

### Post by murderslastcrow on 2010-01-20
Pardon me if I'm wrong, but couldn't you simply install x.org, GDM, and fluxbox or whichever so you can install the video driver, then create a startup entry specifically to start only xorg and WoW through Wine after installing it in the fluxbox environment? (or even a regular Ubuntu environment?)

Or do you absolutely NEED a WM to run graphic programs? Isn't GDM a graphical program? I think, since the WoW client is free, this would be an awesome idea- a WoW CD you can boot from on any PC. (however, we must take into account that, with all the expansions, WoW is about 30 GB of space, so you'd need a BluRay, but still an interesting concept XD).

Once you have that all set up, you could just set it to start up automatically! Push power button, play WoW. What could be simpler?

Someone please tell me if I'm missing something obvious here.

---

### Post by Grenage on 2010-01-20
Being an MmoRPG, about 500GB of updates to download? ;)

---

### Post by Panties on 2010-01-22
> **tommcd said:**
> Well, since you said in your first post that you wanted a core i7 CPU you will need one of the chipsets that support it. Phoronix has done some reviews of the P55 chipset and the X58 chipset using core i7 CPUs on Ubuntu:
[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1)
I think the X58 chipset is more performance oriented than the P55. Motherboards with the X58 chipset may be more expensive though.
For specific motherboard recommendations and the like, you can try asking on the Phoronix forums. You will likely find people there with experience running core i7 in linux.


Unfortunately, My local computer store "DO NOT" sell ICore7 Yet! :( They were out of stock! SAD!!!!! They mention it will take 2 weeks, for the shipment to come in! I cannot wait that long! XD

Alternatively, I got myself a new Core 2 Duo QUAD, Extreme Processor! I got myself a graphic card, Nvidia GTX295. Exactly the one in Youtube (I plan to install tonite, will keep you posted!):-
[COLOR=#0000FF][FONT=Tahoma]http://www.youtube.com/watch?v=KhS8qJzGKCg


[/FONT][/COLOR]

---

### Post by Panties on 2010-01-22
> **murderslastcrow said:**
> Pardon me if I'm wrong, but couldn't you simply install x.org, GDM, and fluxbox or whichever so you can install the video driver, then create a startup entry specifically to start only xorg and WoW through Wine after installing it in the fluxbox environment? (or even a regular Ubuntu environment?)

Or do you absolutely NEED a WM to run graphic programs? Isn't GDM a graphical program? I think, since the WoW client is free, this would be an awesome idea- a WoW CD you can boot from on any PC. (however, we must take into account that, with all the expansions, WoW is about 30 GB of space, so you'd need a BluRay, but still an interesting concept XD).

Once you have that all set up, you could just set it to start up automatically! Push power button, play WoW. What could be simpler?

Someone please tell me if I'm missing something obvious here.


1. YOU GOT IT! Yes, I turn on my button, and it loads WOW! AT STARTUP! That's what I want! Do you have any suggestion on how am I going to do that? I downloaded several  Ubuntu Distros and already burned them! Ubuntu Desktop Lite, Ubuntu Desktop and Ubuntu Server. All are version 8.04. Should I install Ubuntu Server and slowly use apt-get to install those package? Can you advice me how do get it done? Im not really an expert in UBUNTU or any linux command... but I am willing to learn! How to put them on startup? what apt-get command should i use? what WM should i get? how how how?


2. Nope, NO blueray..... Dont want those... I am not planning to start a game from a blueray disc....

3. "Once you have that all set up, you could just set it to start up automatically! Push power button, play WoW. What could be simpler?" YES, I want this...

---

### Post by Panties on 2010-01-22
> **Grenage said:**
> Being an MmoRPG, about 500GB of updates to download? ;)

Yeah, Wow is a big game, and need some commitment too. But I just love that game.. =)

---

### Post by hectic1 on 2010-01-23
am i the only one who thinks that whole idea is really stupid?
first of all no linux can not be faster in gaming than windows on the same machine and uses more resources,2nd it's just f*in wow you don't need a 5000$ pc
or whatever and 3rd u can't even call it a gaming rig!

---

### Post by cascade9 on 2010-01-23
> **tommcd said:**
> The Intel core 2 duos and newer core i7 CPUs are supposed to offer much better performance than the AMD Phenom CPUs. The Intel chipsets tend to work well on linux also. For a high performance gaming rig I would think Intel would be the way to go.
The late model Intel CPUs are more expensive than the AMD CPUs though.

Depends on what your looking at. The AMD X4 965s actually get better framerates on a lot of games compared to the i7s, let alone the older, slower Core2Duos. 

I've had no issues with the ATI or nVidia chipsets for AMD I've used under linux. 

> **Panties said:**
> To answer your question, My goal is to turn a PC, into a gaming console, since there are no OS that does that.... (OS which dedicate for gaming only!)

There is actually- linux-gamers 

[http://live.linux-gamers.net/](http://live.linux-gamers.net/)
[http://distrowatch.com/table.php?distribution=linuxgamers](http://distrowatch.com/table.php?distribution=linuxgamers)

> **Panties said:**
> Unfortunately, My local computer store "DO NOT" sell ICore7 Yet! :( They were out of stock! SAD!!!!! They mention it will take 2 weeks, for the shipment to come in! I cannot wait that long! XD

Alternatively, I got myself a new Core 2 Duo QUAD, Extreme Processor! I got myself a graphic card, Nvidia GTX295. Exactly the one in Youtube (I plan to install tonite, will keep you posted!):-
[COLOR=#0000ff][FONT=Tahoma]http://www.youtube.com/watch?v=KhS8qJzGKCg
[/FONT][/COLOR]

Pity...the Core2Quads are OK for gaming, but the GTX295 is a pain in the butt. SLI on a card always is.... Its wayyyy overkill for WOW as well, a nice GTX260 to GTX285 would work just as well, with less heat and less power consumption.

---

### Post by Panties on 2010-01-23
> **hectic1 said:**
> am i the only one who thinks that whole idea is really stupid?
first of all no linux can not be faster in gaming than windows on the same machine and uses more resources,2nd it's just f*in wow you don't need a 5000$ pc
or whatever and 3rd u can't even call it a gaming rig!

I think you're wrong. There are no ideas that it is called "s2upid". 
How can you say things that are "s2upid" which you have not tried it yet?
If you think this is really s2upid, you shouldn't be here to leave any comments. There are other forums which requires your attention! Not here, not this post! :(

"No Linux can not be faster in gaming than windows...", its like you are absolutely sure that Linux have no room for gaming? even if in the near future of say Year2030? Poor Linux, Gaming for Linux is near Doom... is not even possible... :confused:

And as for gaming rig... I previous own 3Ghz P4 HT with ATI 9800XT, was a gaming rig during the it's era. It was the TOP of the league! Unfortunately, that computer's era ended, and more advance gaming requires more computer power to play on!:P

Now I need a stronger computer, far more advance, and I have that 5000$ to play my wow. Gaming rig or not, its my computer, not yours. I need help in setting up a computer and I am interested to contribute to opensource OS, to play my games. If you're here to help me set it up, I be happy to share with the community... however, if you're here to complaint about gaming in linux(ubuntu), ... you are not helping... :)

---

### Post by Panties on 2010-01-23
> **cascade9 said:**
> Depends on what your looking at. The AMD X4 965s actually get better framerates on a lot of games compared to the i7s, let alone the older, slower Core2Duos. 

I've had no issues with the ATI or nVidia chipsets for AMD I've used under linux. 



There is actually- linux-gamers 

[http://live.linux-gamers.net/](http://live.linux-gamers.net/)
[http://distrowatch.com/table.php?distribution=linuxgamers](http://distrowatch.com/table.php?distribution=linuxgamers)



Pity...the Core2Quads are OK for gaming, but the GTX295 is a pain in the butt. SLI on a card always is.... Its wayyyy overkill for WOW as well, a nice GTX260 to GTX285 would work just as well, with less heat and less power consumption.


Hey thanks, I will look into those links right now...

In terms of Nvidia or ATI, I already bought the Nvidia GTX295, I know its a bit overkill for wow.... , but one day, that card will be like 3dFX days.. =)

Im not planning to get SLI though, its eats 630Watts X 2 = 1260 watts.. wow! 
I think one card should do the trick. 


"Depends on what your looking at. The AMD X4 965s actually get better framerates on a lot of games compared to the i7s, let alone the older, slower Core2Duos."
 I previously had AMD XP 3000. The only thing I am not comfortable with AMD, its that the chip gets very hot. My room gets very hot even if the air-cond was turn on. Thus, I dont know about you, but in my experience, the intal processors tend to be more stable than the AMD....

I try to get a picture of my computer and post it up as soon as I fix it up! =) I am still trying to figure out, which Linux Window Manager GUI, should I use. I have 3 Harddrive in that computer, 2 for linux, 1 for windows.. any doubts/suggestionson which OS should I install?, are welcome!

---

### Post by cascade9 on 2010-01-23
> **Panties said:**
> In terms of Nvidia or ATI, I already bought the Nvidia GTX295, I know its a bit overkill for wow.... , but one day, that card will be like 3dFX days.. =)

Im not planning to get SLI though, its eats 630Watts X 2 = 1260 watts.. wow! 
I think one card should do the trick. 

Umm...the GTX295 IS SLI on a single card. Its 2xGTX 275 chips on one card.

> The two GPUs used in the GeForce GTX 295 have specifications that sit between the GeForce GTX 260 and GTX 280.[http://www.legitreviews.com/article/863/1/](http://www.legitreviews.com/article/863/1/)

As for 1260 watts....LOL. No way. A loaded up system with a GTX295 draws about 500watts, max.

[http://www.xbitlabs.com/articles/coolers/display/system-wattage_8.html#sect0](http://www.xbitlabs.com/articles/coolers/display/system-wattage_8.html#sect0) 

> **Panties said:**
> I previously had AMD XP 3000. The only thing I am not comfortable with AMD, its that the chip gets very hot. My room gets very hot even if the air-cond was turn on. Thus, I dont know about you, but in my experience, the intal processors tend to be more stable than the AMD....


Funny enough, I've run both P4 HT 3Ghz and XPs of various types (never actually had a 3000+ but I ran an overclocked 2500+ at 3000+ and 3200+ speeds) and I found that the Athlon put out a lot less heat than the intel. 

I also found that AMD XPs were more stable than P4s in general.

> **Panties said:**
> And as for gaming rig... I previous own 3Ghz P4 HT with ATI 9800XT, was a gaming rig during the it's era. It was the TOP of the league! Unfortunately, that computer's era ended, and more advance gaming requires more computer power to play on!:P

That system still has more power than you'll need for WoW. ;)

---

### Post by cdk on 2010-01-23
This is a pretty good laugh.

Good troll!

---

### Post by Panties on 2010-01-23
> **cascade9 said:**
> Umm...the GTX295 IS SLI on a single card. Its 2xGTX 275 chips on one card.

[http://www.legitreviews.com/article/863/1/](http://www.legitreviews.com/article/863/1/)

As for 1260 watts....LOL. No way. A loaded up system with a GTX295 draws about 500watts, max.

[http://www.xbitlabs.com/articles/coolers/display/system-wattage_8.html#sect0](http://www.xbitlabs.com/articles/coolers/display/system-wattage_8.html#sect0) 



Funny enough, I've run both P4 HT 3Ghz and XPs of various types (never actually had a 3000+ but I ran an overclocked 2500+ at 3000+ and 3200+ speeds) and I found that the Athlon put out a lot less heat than the intel. 

I also found that AMD XPs were more stable than P4s in general.



That system still has more power than you'll need for WoW. ;)


Yeah, I know the card has 2 GPU inside GTX295. But I read the zoltac manuals, it says here, in page 3, it requires 630 Watts PSU. U sure is 500 Watts only? What happen to the card, if it runs below the required Watts? Kaboom? ;)

I am using a P4 3Ghz HT right now, I did install the WOW and been playing for quite 3 years. Honestly, when Wrath Of the Lich King, in Dalaran, I could feel the graphic lag. It's just soo annoying, when you run in Dalaran with only 5-10 FPS.... 
Burning Crusade and Classic Maps, are great though with decent 30Fps...
Im running a Intel 865 Chipset, 2 GB ram (Dual Channel)... still lag in Northerend.. :(

I do love AMD, dont get me wrong! I love both equally. AMD was my gaming machine too. 1 thing I love about AMD over Intel, is the overclocking capabilities. I think in my life, I have fried 5 Durons, 2 K2's, 1 XP, 5MPs. With various motherboards, during my younger days. Yeah, I was notti and rich enough to spend all those processors!

For intel, Most of the BIOS are lock! Hence wait! I think I did overclock Pentium 1 before or was it a Celeron.... I increase the FSB too! using those Jumpers on the motherboard...

I think Overclocking wise, AMD is the way to go... (for gaming too)

Anyway, Im building the PC, with 3 HDD and 1 DVD Burner... Should it be enough? Should I get SCSI over SATA ?

---

### Post by Panties on 2010-01-23
> **cdk said:**
> This is a pretty good laugh.

Good troll!


I do want to Game on linux machine! Enough of Microsoft.
Time to learn new stuff.... XD

---

### Post by cascade9 on 2010-01-23
> **Panties said:**
> Yeah, I know the card has 2 GPU inside GTX295. But I read the zoltac manuals, it says here, in page 3, it requires 630 Watts PSU. U sure is 500 Watts only? What happen to the card, if it runs below the required Watts? Kaboom? ;)

Depends. On the test that I linked to, a full system used on 500watts, 'from the wall'. That would end up being about 450watts from the power supply. But I wouldnt try running a GTX295 on less than 600+ watts power supply. But..if it came down to it, I would rather try to run a GTX295 on a decent brand power supply rated at 550watts rather than some cheap junk rated at 750 ;) Power supplies quality varies a lot, which is why you will see different 'minimum power supply' on different manufacturers pages.  

BTW, nVidia says 680watts- 

> Maximum Graphics Card Power (W)289                               W                           Minimum System Power Requirement (W)680                               W                           [http://www.nvidia.com/object/product_geforce_gtx_295_us.html](http://www.nvidia.com/object/product_geforce_gtx_295_us.html)

But even if you believe 630 watts minimum, running 2 wouldnt make it 2x630watts. That 630 watts figure has to cover everything else in your computer- CPU, RAM, sound card, network, hdds and CD/DVD drives. Since you are only putting 1 more card in, not a whole new computer, it would be far less than 2x630 ;) 

As for what would happen if yuo didnt have enough power......that depends as well. 'kaboom' is unlikely. 'fizzle fizzle OMG my computer just shut down for no reason' is likely. 'What the heck is happening, now it doesnt want to start again' is always possible....

> **Panties said:**
> Anyway, Im building the PC, with 3 HDD and 1 DVD Burner... Should it be enough? Should I get SCSI over SATA ?

SCSI is....err.....to expensive. SAS (Serial Attached SCSI) is whats becoming more common. I dont know if I would bother with that though, SATA does fine. 

If you've got money to spend, SSDs (solid state drives) are faster than SATA, SAS or SCSI Hdds (maybe not full 15K fibre SCSI, but who has the money for that?). They are pretty expensive for the larger ones though, so your better off with a small SSD (for your OS) and a big HDD or 2.

---

### Post by Panties on 2010-01-24
> **cascade9 said:**
> Depends. On the test that I linked to, a full system used on 500watts, 'from the wall'. That would end up being about 450watts from the power supply. But I wouldnt try running a GTX295 on less than 600+ watts power supply. But..if it came down to it, I would rather try to run a GTX295 on a decent brand power supply rated at 550watts rather than some cheap junk rated at 750 ;) Power supplies quality varies a lot, which is why you will see different 'minimum power supply' on different manufacturers pages.  

BTW, nVidia says 680watts- 

[http://www.nvidia.com/object/product_geforce_gtx_295_us.html](http://www.nvidia.com/object/product_geforce_gtx_295_us.html)

But even if you believe 630 watts minimum, running 2 wouldnt make it 2x630watts. That 630 watts figure has to cover everything else in your computer- CPU, RAM, sound card, network, hdds and CD/DVD drives. Since you are only putting 1 more card in, not a whole new computer, it would be far less than 2x630 ;) 

As for what would happen if yuo didnt have enough power......that depends as well. 'kaboom' is unlikely. 'fizzle fizzle OMG my computer just shut down for no reason' is likely. 'What the heck is happening, now it doesnt want to start again' is always possible....



SCSI is....err.....to expensive. SAS (Serial Attached SCSI) is whats becoming more common. I dont know if I would bother with that though, SATA does fine. 

If you've got money to spend, SSDs (solid state drives) are faster than SATA, SAS or SCSI Hdds (maybe not full 15K fibre SCSI, but who has the money for that?). They are pretty expensive for the larger ones though, so your better off with a small SSD (for your OS) and a big HDD or 2.



SATA it is then... :) I have a Golden Question....... ->

---

### Post by Panties on 2010-01-24
Sorry, not Golden Question.. XD
Bronze Question:-
Upon Installing Ubuntu & Research...

1. OS: I have 4GB of RAM, I should go for UBUNTU 64 bit right? There are 2 versions of Ubuntu over there...
Download Ubuntu 9.10 
Download Ubuntu 8.04 LTS 

When I boot 9.10, My keyboard doesn't work on the installation.. :(
But Ubuntu 8.04, works fine.

Should I go for a 64 bit? or stick with 32 bit for gaming?

2. Harddisk: For Linux SWAP, should I dedicate 1 entire Harddisk (160GB) just for swap? and then use JFTS or Reizer partitions for another HDD? (I'm noob, I know)

3. CrossOver Vs Cedega Vs Wine.
Hard Choice.... which one works best for emulating Dx9 or OpenGL? Whichs works very well for World of warcraft?:confused:

---

### Post by cascade9 on 2010-01-24
> **Panties said:**
> 

1. OS: I have 4GB of RAM, I should go for UBUNTU 64 bit right? There are 2 versions of Ubuntu over there...
Download Ubuntu 9.10 
Download Ubuntu 8.04 LTS 

When I boot 9.10, My keyboard doesn't work on the installation.. :(
But Ubuntu 8.04, works fine.

Should I go for a 64 bit? or stick with 32 bit for gaming?

No idea whats stopping your keyboard from working (I would probably consider making a separate thread about that). 32bit should work fine, and I doubt you would get anything out of 64bit gaming in linux. I would probably still run 64bit, myself....but you might find 32bit easier. 

> **Panties said:**
> 
2. Harddisk: For Linux SWAP, should I dedicate 1 entire Harddisk (160GB) just for swap? and then use JFTS or Reizer partitions for another HDD? (I'm noob, I know)

Noes! if you have 4GB of RAM, I wouldnt make the swapfile any bigger than about 6GB. Riser FS is pretty much dead now. JFS is a good filesystem, but EXT3/4 would be my choice. 

> **Panties said:**
> 
3. CrossOver Vs Cedega Vs Wine.
Hard Choice.... which one works best for emulating Dx9 or OpenGL? Whichs works very well for World of warcraft?:confused:

I've heard cedega works well with WoW. But you shouldnt have any issues with WINE. I'd at least try WINE before trying cedega.

---

### Post by Clopin on 2010-01-24
I have not read all of the replies yet, so if it has already been answered, I am sorry.
For starting WoW on (Ubuntu) startup, couldn't you just add it to System -> Preferences -> Startup Applications?

Name: WoW
Command: "/home/USERNAME/.wine/drive_c/Program Files/World of Warcraft/Wow.exe" -opengl
Comment: Start WoW

---

### Post by Panties on 2010-01-24
[cascade9]("http://ubuntuforums.org/member.php?u=890788")

Thanks.. I will be bz fixing up the machine.. its going to take some time. I wonder if this UbuntuForum, able to post picture? or should I use Photobucket and link it here?



[Clopin]("http://ubuntuforums.org/member.php?u=763414")

Oh, but I need to write a small script, right? to sleep for at least 30 seconds before it loads wow? This will allow the drivers to load properly, right?

---

