---
title: "How can I make Ubuntu Mate look like Solus Mate?"
date: 2023-08-29
forum: Desktop Environments
---

### Post by kwanbis on 2023-08-29
I want to move one of my machines to Ubuntu Mate, however, I find a problem with the way Mate is configured: you have a panel on the bottom and a panel on the top, which added to the program title bar, wastes a lot of space for my taste.

I was testing distros and I found out that what I want is how Solus has configured Mate, as it is closer to the way I work today. It looks very much like Windows, which is a configuration I find very logic to me: only one taskbar, star menu bellow, system tray etc.

By the way, I know KDE is closer, but the problem is the way it handles many open windows: Solus-Mate keeps making the icons smaller, and smaller, just like windows. KDE, as soon as you hit 5 or 6 open windows of the same program, it combines them into one, and I don't like that. 

However, since I am more used to Ubuntu, I was wondering if anybody know how to replicate what they have done in Solus-Mate? Thanks.
[https://imgur.com/34xX4wE.png](https://imgur.com/34xX4wE.png)

[https://imgur.com/YeSG5Vn.png](https://imgur.com/YeSG5Vn.png)

[https://imgur.com/qTuDe33.png](https://imgur.com/qTuDe33.png)

---

### Post by guiverc on 2023-08-29
Have you tried looking at what the Solus system uses, what apps etc. are used.

I've no experience with Solus myself, but I've have moved Fedora, OpenSuSE, Linux Mint, Debian & CentOS systems to Ubuntu and kept the same configs so the operation remained the same (*only OS underneath the desktop changed to a Ubuntu base*). 

Some *distributions* also alter some components, eg. I'm using Lubuntu currently; which means I'm using a LXQt desktop and using Openbox as my WM. If I was to install Debian with LXQt that system would not install with Openbox but xfwm4 as the default WM; ie. I'd also have to change the default WM to get the same operation between Ubuntu and Debian with LXQt. It's tiny differences like that, plus configs/themes etc that are all I'd expect. Comparison should show these rather easily I suspect.  Have you looked

If you'd like to replace an existing Solus system with Ubuntu (inc. Ubuntu-MATE !) I've written an answer here that maybe useful - [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)  being what I used to convert OpenSuSE/Fedora/Debian/CentOS/..  that I have switched to Ubuntu systems and having the same operation.

I reinstalled a system today; and whilst almost everything looked good.. it still looked *slightly* different.. until I realized I'd omitted a font (*thus text looked slightly different*). Those *little* details (what theme, what font, DM being used, etc) usually aren't difficult to spot; keep a Solus setup on another nearby box or VM until you've worked out the *tiny* differences.

MATE allows easy configuration of many *default* setups, and both do NOT use two panels. What you're after maybe just as easy as changing the theme.  Note:  *theme options vary on release of MATE being used, thus release of Ubuntu/Ubuntu-MATE matters in contrast to version of MATE in Solus. Newer MATE has dropped two themes if I recall correctly.*

[https://guide.ubuntu-mate.org/](https://guide.ubuntu-mate.org/)

---

### Post by kwanbis on 2023-08-29
Thanks.

I normally try to use the systems with the least changes as possible. Not because I don't know how to or I cannot learn to do it, but because the more things I need to change, the more work each time I have to install/reinstall. 

But in this case, the way Solus' Mate works, is so so much how I like it, that is crazy.

I have no idea what the Solus system uses, what apps etc. I mean, I know I downloaded the MATE version (I tried the KDE version, but the way KDE handles the task bar is not how I like it).

If I was to compare, how should I? Is it about config files? Or is it about something else?

I would try the themes part and get back here if I can't fix it. Thanks for responding.

---

### Post by simonsaysthis on 2023-08-30
Hello. This will be fairly easy to do. Step 1 is install Ubuntu Mate. Step 2 would be to use the same theme. I will have a look which themes they use and write back. You should be able to extract all the relevant info from the live session but I'll have a look for you now...

---

### Post by simonsaysthis on 2023-08-30
You basically need these two themes 1) Qogir Dark GTK3 theme 2) Papirus Dark icon theme

---

### Post by guiverc on 2023-08-30
> **kwanbis said:**
> 
If I was to compare, how should I? Is it about config files? Or is it about something else?

I would try the themes part and get back here if I can't fix it. Thanks for responding.

You've already got an answer related to the themes, but you can gain a lot of knowledge about the system with some very simple (and common) tools.

eg.

```

guiverc@d7050-next:/lts/home/guiverc$   neofetch --off
guiverc@d7050-next 
------------------ 
OS: Lubuntu Mantic Minotaur (development branch) x86_64 
Host: OptiPlex 7050 
Kernel: 6.3.0-7-generic 
Uptime: 1 day, 50 mins 
Packages: 2935 (dpkg), 11 (snap) 
Shell: bash 5.2.15 
Resolution: 1920x1080, 1920x1080, 1920x1080, 1280x1024, 1280x1024 
DE: LXQt 1.3.0 
WM: Xfwm4 
WM Theme: Pills 
Theme: Greybird [GTK2/3] 
Icons: oxygen [GTK2/3] 
Terminal: qterminal 
Terminal Font: IBM Plex Mono Text 14 
CPU: Intel i5-6500 (4) @ 3.600GHz 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
GPU: Intel HD Graphics 530 
Memory: 5642MiB / 15842MiB 

```

This shows my OS/release, desktop, my WM, themes detail etc.  (*I only used --off as the ascii logo doesn't help here*)

By comparing that to a *live* system of Lubuntu *mantic* I'd expect to see differences in the WM, my themes, my terminal font etc.

Yes on occasion little differences may require me to go further, eg. if a specific app is different I'd likely compare versions of the app which may explain it.. or even dig down into .conf files for some apps; but most differences can be detected by info tools like `neofetch` I used above easily. Whilst `neofetch` won't show many font values (*terminal is shown only*), those *fonts* are usually pretty easy to detect & explore using the DEsktops own setting tools.

*ps:  when screenshots are posted; they often include `neofetch` in the screenshot as it saves people from asking what font/theme/wm etc was being used & thus saving replies...*

---

### Post by simonsaysthis on 2023-08-31
[QUOTE=

*ps:  when screenshots are posted; they often include `neofetch` in the screenshot as it saves people from asking what font/theme/wm etc was being used & thus saving replies...*[/QUOTE]

Haha how did I even forget about neofetch. Would have saved me lots of work with the screenshots. Anyways, I think OP is not too used to theming so I guess the screenshots will help.

---

### Post by kwanbis on 2023-09-01
OK, so you say that by applying those two themes, the bar on top would disappear and I would only have one panel then?

---

