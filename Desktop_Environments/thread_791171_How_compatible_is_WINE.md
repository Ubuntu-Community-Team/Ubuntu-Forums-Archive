---
title: "How compatible is WINE?"
date: 2008-05-11
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-05-11
Feel free to move this thread if I misposted, seems like the right one though.

Anyways, I'm using Windows Vista and I'm getting more and more disgusted by it every day.

My question is: How well does WINE work? Does it work exactly as if I had XP installed? Does it run Java? 

C++? Are there programs that will run in windows but not WINE? Vice versa?

If wine works well enough I wouldn't mind switching to linux, my system resources would certainly thank me.

---

### Post by Barriehie on 2008-05-12
I too became disgusted with the bloat and one morning blew away XP Pro SP2 and went totally Ubuntu.  I've found that wine ran my favorite editor and all other apps have been replaced with native ones.  The only program it won't run for me is FS2004, since it's a game I'm only lacking in recreation on this box! 

My editor has since changed to Bluefish and my databases recreated with SQL.  About a month of changeover but I feel more secure with this OS running things.  It's not **[COLOR=Red]flaky[/COLOR]**[COLOR=Red][COLOR=Black].[/COLOR][/COLOR]

Barrie

---

### Post by Victormd on 2008-05-12
Wine is pretty compatible (as far as common appz go). You can check out a list of appz at [www.winehq.org](www.winehq.org) to see if it'll meet your needs. However, if the software you need is not listed, you can be sure that there is a native alternative to it and you're better off using that. this screen shot should give you an idea of what it can do... I have programs running with wine and an XP running with Virtualbox... so you can see that you have alternatives if strictly necessary...

---

### Post by Victormd on 2008-05-12
Barrie,
Running games under a virtualized environment (i.e., virtualbox, vmware) is no good. Unfortunately, you won't have hardware support (i.e., graphics card does not support 3D) so your games might not even run. I would check the winehq.org [application database]("http://appdb.winehq.org/") to see if your game is listed and if so, go with wine, otherwise, dual-boot. For my games, that's what I do, and that's all I use windows for...
(answered through here to help others with similar questions)

---

### Post by SimbaSpirit on 2008-05-12
I use 3d studio max 2008, and would be willing to revert to 9.

The appdb says its at best bronze. 
Is that db the definitive updated guide or is it possible things are working better now than is listed?

Switching to blender from max would be very time costly, which is something I can't really afford.

---

### Post by SimbaSpirit on 2008-05-12
Ok virtualbox, I've heard of it but never actually used it.

As I understand it its a low-level resource manager allowing you to dual boot.

Just how resource-intensive is that? Sounds like it would chew through RAM like there's no tomorrow. And how quickly does it toggle between OS's? Is it as fast as alt+tabbing, or does it take loading time?

I have an inspiron 1521
1.5 GB ram
dual core 1.9Ghz AMD processor
x1270 gfx card
120 GB SATA hdd

See any problems in the hardware specs? Besides that it's a dell ;)

---

### Post by galileon on 2008-05-12
virtual box runs like a simple application, except that it runs windows inside... switching to it works just like alt-tabbing to another window...i've had problems runinng itunes on windoze in it, but otherwise most programs run fine...

---

### Post by Victormd on 2008-05-12
> **SimbaSpirit said:**
> I use 3d studio max 2008, and would be willing to revert to 9.

The appdb says its at best bronze. 
Is that db the definitive updated guide or is it possible things are working better now than is listed?

Switching to blender from max would be very time costly, which is something I can't really afford.

The database and ratings can be as old as the first release of WINE. Some appz are rated by the developers and others by users, and the WINE version used is also listed. The latest release is 1.0RC1, so if the app. was tested with something earlier, it might be working now. As for 3dsMAX, I gotta tell you that I was never able to get it to work, and under virtualbox, well, gotta use software rendering because of the lack of 3D support.

Also, Virtualbox is not a dual-boot, it's a virtualization of an OS so you run windows (or any other OS) as a program inside a virtual machine in ubuntu, and yes, it does use up resources, but you can tune it specifying the amount of RAM, video mem and things like that that will make run a bit smoother.

NOTE: Someone please correct me if there's an alternative for 3D support under virtualbox...

---

