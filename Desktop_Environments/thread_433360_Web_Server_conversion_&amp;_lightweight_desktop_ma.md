---
title: "Web Server conversion &amp; lightweight desktop manager"
date: 2007-05-04
forum: Desktop Environments
---

### Post by wordsmithereens on 2007-05-04
Hi all;

I'll be converting a web server from Win 2003 to Ubuntu or some other Linux flavor in the next while. 

It has been recommended to me to install the server version of Feisty with LAMP or some portion thereof. This will be a web site with 99.99% straight HTML and .01% javascript - really nothing that's too processor intensive or even TCP-intensive - 2000 -3000 page hits a day, some downloads of ZIP and HQX files.

I installed and ran the Feisty server version in VMWare Workstation, but I'm not sure I'd be completely comfortable or confident going from a graphic environment with command-line capabilities (such as they are ...) in Win 2003 to a completely CLI-based environment ... yet.

Given that the site is not terribly busy and that the machine is reasonably fast (Athlon XP+2600, 1.2 gig RAM) would a regular version of Feisty, or maybe one with a :lighter" desktop manger (XCE?  other?  be more appropriate?

I intend to learn more about a CLI based environment as I go along, but would rather make the move away from MS to Linux sooner than later, if you know what I mean. 

TIA for any comments or suggestions. 8-) 

~ wordsmithereens ~

---

### Post by Spacen on 2007-05-06
If you install the server version you can then go on to install the standard desktop via:

sudo apt-get install ubuntu-desktop

however, it installs a bunch of stuff including open office and all the rest, so this may not be the best way to go.

I am also looking for a light window manager for the server installation. I've not come up with anything yet -- I have to remove ubuntu-desktop first to try stuff out.

---

### Post by RedSquirrel on 2007-05-07
I use Fluxbox as my light window manager on top of Ubuntu server. I just install other apps with apt-get as I go along.

---

### Post by wordsmithereens on 2007-05-07
Thanks - maybe I'll give that a try.  I have the server version in a VM right now so it'll be a quick experiment. 

~ wordsmithereens ~

> **RedSquirrel said:**
> I use Fluxbox as my light window manager on top of Ubuntu server. I just install other apps with apt-get as I go along.

---

### Post by obrient on 2007-05-07
I have been running a web server with an old Dell with 384 MB of RAM, granted I believe my page views are less (21314 in the month of April), but I have had great success with my Fedora server setup with the GUI and will be moving it to Ubuntu eventually. 

I have Gnome Window Manager running on it and don't notice too much of a lag. It isn't a production site, but a personal site so I am okay with a bit slower response. I also stream music over it without much of a problem. 

I have a test box running inside my personal network with Ubuntu Desktop and the LAMP stack where I have been running Media Wiki and other PHP based apps and that machine curns just fine. I would say with the machine you have you should be okay with the GUI on top.

---

### Post by wordsmithereens on 2007-05-07
That's good to know. I figured too that I have already been running it inside a GUI (Windows 2003 Server) fro a few years, so Ubuntu should be better across the board. 

I'm also looking at an Open SUSE 10.2 installation and will be installing it to a VM in the next few days to check it out.  I understand there are several desktop choices during install - Gnome, KDE or ... maybe Fluxbox , cant recall at the moment. 

Thanks!

~ wordsmithereens ~

---

