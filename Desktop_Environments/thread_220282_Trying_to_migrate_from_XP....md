---
title: "Trying to migrate from XP..."
date: 2006-07-21
forum: Desktop Environments
---

### Post by mwob on 2006-07-21
Hi there,

I tried installing Ubuntu to see what all the fuss was about. I have since become quite a big fan of it and the linux OS in general... There are some common tasks that I do in windows that I would like to do in linux, but I don't know what software to use or how to go about it.. If anyone can help with any of these I'd be very appreciative, and you'd be helping foster a linux user ;)

Here goes...

1) Media player. I use winamp in windows. I want a similar tool that keeps a "library" of my meda files and plays mp3s/wmas nicely...what should I use?

2) UTorrent. Is there a good equivilent to this nice small BitTorrent client in linux?

3) .NET. As a .NET developer, I obviously need to use MONO. But I was wondering if its possible to run visual studio inside linux....would something like WINE manage that?

Thanks!

---

### Post by loell on 2006-07-21
these are just my personal preferrence and/or  opinion
1.banshee player

2.qtorrent

3. i think its possible to run visual studio in wine, though i just doubt if there's someone serius in development uses this setup, plus the caveats that it may have. yes mono might be the answer, but it still young, and if your a click,drag,double click and code person, then you might be disappointed in mono. i would suggest just dual booting if you're into .net development.

---

### Post by Kelnoky on 2006-07-21
Hey there and welcome to ubuntu, have a nice time. :)

1. There are a bunch of good players out there. My favorite one is amarok, works great for me. :) You could also try the Rythmbox Music player, it also has a library for the files.

2. Aye, KTorrent. :) At least it works good for me, better than any torrent on windows. *g*

3. Sorry, no idea pal. :D

---

### Post by shawnrgr on 2006-07-21
For bittorrent i would you Azureus. Its not the smallest but its not to bloated, and I have never hand any problems with it. Or if you want really simple and little options, just install "BitTorrent" from the internet section. But you don't have much control over it.

For winamp-like media player with library, use amaroK. Or just stick with Rythmbox, its all I use.

For .NET, I was going to tell you MONO lol.  As for it working under wine.. im not sure of that. maybe someone else here can help with that one

---

### Post by krismatth3 on 2006-07-21
> **mwob said:**
> Hi there,
3) .NET. As a .NET developer, I obviously need to use MONO. But I was wondering if its possible to run visual studio inside linux....would something like WINE manage that?


I have not seen a succesful install of VS.Net in Linux. However, check out MonoDevelop: [http://www.monodevelop.com/Main_Page]("http://www.monodevelop.com/Main_Page")

[IMG]http://www.monodevelop.com/files/9/93/Md-main.png[/IMG]

---

### Post by mwob on 2006-07-21
Thanks all for the responses, you're all very helpful :)

I'll check out those players, and maybe give MonoDevelop a good look....

Cheers

---

### Post by krismatth3 on 2006-07-21
monodevelop is in Universe I believe - so if you enable the universe repository, you can just do a "sudo apt-get install monodevelop" (or via synaptic - System->Administration->Synaptic Package Manager)

---

### Post by pzonik on 2006-07-21
1) Media player. 

BMPX is very good. 
[http://beep-media-player.org/site/BMPx_Homepage](http://beep-media-player.org/site/BMPx_Homepage)
In 'download' section you can find easy Ubuntu how-to.

I also use sometimes BMP and XMMS (are in repositores) and I heard about XMMS2.

2) Torrent

Standard Gnome client is light and easy to use, but is a litlle different from uTorrent. For KDE you can use ktorrent.

---

### Post by ovistanciu on 2006-07-21
hi there!

i'm actually doing the same thing: i'm a .NET developper, using Linux at home (more than Windows - i dual boot - this is the best solution for me). 

so let me give some suggestions:
1)XMMS. It looks and works alot like Winamp. But Winamp and XMMS will seem lame once you try amarok. it has much more to offer than good ol' winamp.
2)Azureus. i use it also in windows. it's Java, so it's cross platform. you'll have no problems (or less problems, to be realstic :) )
3)as loell put it before me, Mono is nice, but limited. the best solution is to dual boot. 

i wish you the best of luck.

---

### Post by Thund3rstruck on 2006-07-21
> 
.NET. As a .NET developer, I obviously need to use MONO. But I was wondering if its possible to run visual studio inside linux....would something like WINE manage that?

I'm a .NET developer as well and I've tried just about everything I could find but for me there really is no alternative to VS2003/2005 in Windows. VMWare sessions are just too slow to run it properly and Mono, while impressive is not quite there yet. 

If you're squarly ASP/C# for the web, you may do just fine but my specialization (desktop/network programming in C#.NET and VB.NET) its become too tedious copying over code to debug and test on wintel platforms. 

Personally, I have accepted the fact the I must keep at least one machine windows in order to accomplish my work related tasks and Linux on all my personal machines.

---

### Post by krismatth3 on 2006-07-21
> **Thund3rstruck said:**
> Personally, I have accepted the fact the I must keep at least one machine windows in order to accomplish my work related tasks and Linux on all my personal machines.

I used to feel that way - until I tried out VMWare Server: [http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server"). I installed Ubuntu 6.06 on what was previously my windows dev machine, then installed VMWare Server on it. I connect to the server with "VMWare Server Console" from my main Linux box, and speed wise you cannot tell that it's remove (over my LAN, anyway). I run VC6, VS2003, and VS2005 on it for work - it responds well even under heavy load. (Desktop apps, COM components, C++ Webservices and .Net webservices if you're curious.)

---

### Post by mwob on 2006-07-21
Yep, MONO looks OK and getting better, but once you're used to the features of VS2005 you kind of need them, and mono lacks a lot of that obviously.

---

### Post by mwob on 2006-07-21
VMWare Server looks interesting, but I think dual boot is the way to go for me.

Actually, have any of you windows users managed to connect to a remote windows PC? In XP I have a VPN connection to the office, and once connected I use "Remote desktop connection" to connect and control my work PC.. Is the same kind of think possible with linux?

---

### Post by Thund3rstruck on 2006-07-22
I actually haven't tried using VMServer from a remote machine (as it was intended to be used) so I may just try that (running it locally is just too slow with VS2003). 

Here in august, 100% of my development will involve me using the remote VPN connection back into my companies network so I guess I'll see how well this will work out then

---

