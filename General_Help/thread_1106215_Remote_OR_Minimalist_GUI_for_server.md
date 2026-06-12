---
title: "Remote OR Minimalist GUI for server?"
date: 2009-03-25
forum: General Help
---

### Post by fuzzy1 on 2009-03-25
Hey All,
New to Linux/Ubuntu, I've been happily tinkering with PHP/MySQL on an XP WAMP stack for a few years now (WAMP5 1.74) which includes a Jim-Dandy systray server admin utility for viewing and managing all things server related (e.g. start, stop, config for apache/mysql/php, view logs, add or remove modules etc., along with shortcuts to PMA phpinfo htdocs/wwww folders and more.) 
In short, I really like it. Sadly however, I've come up against a little project for which a windows stack just won't cut it (MPM configuration etc.)

I've a Dual Core Xeon 2.8GHz box with 2Gs RAM, on which I would like to put up a LAMP stack. In fact I had already installed 8.10 server, before learning to my surprise that it did not include any native GUI capability. 
Searching the forums a bit, I soon found instruction for adding ubuntu desktop, and had initiated the installation as such before further reading led me -- only too late -- to the conclusion that this was probably not a great idea (at least for my purposes). I've found a few posts around server GUI, but nothing quite as specific as I was hoping for.

I was hoping that someone here would be so kind as to point me down the shortest path to either a minimalist Ubuntu GUI implementation (allowing for Server Admin et.al  as described above) including a suitable GUI code editor (I like Crimson, Edit Pad and [don't laugh] MS Front page) without unduly impacting server performance. That, OR some means of remotely accomplishing Server Admin et.al in a GUI format as described above, perhaps even from my old familiar XP stomping grounds, leaving the Ubuntu server as CLI only?  Don't get me wrong... I have a passing familiarity with bash commands and can get around well enough to set things up as need be, but for day to day system management, coding and development etc. I am just not at a place where I can devote myself to linux 101, completely re-learning all my bad and hard earned windows computing habits. Could anyone here point me in the direction of such a solution?
Thanks!

---

### Post by Xiong Chiamiov on 2009-03-27
As far as minimalist GUIs go, fluxbox is one of the best.  You really don't need one, though.

Any good editor can edit files over FTP, so all you have to do is set up FTP access on the server.

You'll probably find [webmin](http://www.webmin.com/) very useful.

I found that I didn't know nearly as much about Windows as I thought I did.  I learned more about Linux in the first 6 months using it than in the first 18 years (ok, 5 rather seriously) using Windows.

While you may start with comfy GUI configuration, you will eventually end up a bearded UNIX system administrator, as the terminal is quite more efficient for most system administration tasks.

---

### Post by tsali on 2009-03-27
The biggest resource eater of any linux GUI is the X-Server and an associated VNC server, so if you are going to insist on a GUI, I don't think it matters that much.

I run a Debian home server. I used to run it strictly via CLI (SSH via PuTTY), then installed webmin (wonderful!). It used 144Mb RAM when I was logged in. There were other things I wanted to do, so I installed the GNOME DE and an NX server. This worked very well, using 350Mb RAM when I'm logged in.

---

### Post by fuzzy1 on 2009-03-27
Well thanks to you both. From this and other reading, it looks like wembin comes highly recommended, but I'll look into fluxbox as well.
> I do not use Ubuntu any more, nor have I ever used Gnome.
Care to share with us what you do use? And why?

---

### Post by hyper_ch on 2009-03-27
why do you think you need a gui on a server?

---

