---
title: "Can someone explain ubuntu's family tree?"
date: 2009-01-16
forum: General Help
---

### Post by RandomKillsTime on 2009-01-16
I've done some reading up on this but i don't understand somethings.

Unix was the original>Then someone made a pirated version of it and called it linux>Then people made different skins for linux like ubuntu, kubuntu, xbuntu.

What i don't get is where do terms like gnome, debian and kde fit into this?

---

### Post by amauk on 2009-01-16
Linux is **not** a pirated version of Unix
There is absolutely no Unix code in Linux (that was what the whole court case with SCO was all about)

---

### Post by wolfe on 2009-01-16
I'd suggest going to google and doing a search for the history of linux.  There is far more information out there.

---

### Post by jrusso2 on 2009-01-16
No your idea is all wrong.  Linux is not pirated Unix.  It is written from scratch to be a work a like to Unix.

[http://www.levenez.com/unix/](http://www.levenez.com/unix/)

[http://blog.accurev.com/2008/04/25/forks-feuds-and-friends-the-unix-family-version-tree/](http://blog.accurev.com/2008/04/25/forks-feuds-and-friends-the-unix-family-version-tree/)

The difference between Kubuntu, Ubuntu and xbuntu have to do with the default desktop and apps.

Kubuntu being KDE, Ubuntu, Gnome and Xubuntu, XFCE

---

### Post by RandomKillsTime on 2009-01-16
> **wolfe said:**
> I'd suggest going to google and doing a search for the history of linux.  There is far more information out there.

Yeah. I know and i have done some reading on it but i still don't understand how debian and gnome fit into ubuntu. I was hoping someone could give me a condensed version so maybe i could understand all the info i was reading on the net lol.

---

### Post by capscrew on 2009-01-16
Linux is the kernel only.  Debian is a disto of Linux.  Debian only uses open source software.  Other distros (SUSE and RH) use some closed source software.

Gnome is an open source desktop solution.

Ubuntu is a Debian derivative distro using Gnome as the desktop environment.  Kubuntu is a Debian derivative distro using KDE as the desktop environment.  Xubuntu uses a lightweight X-server desktop. 

A side note to all this:  Debian stands for Deb and Ian Murdock.  Ian started the Debian project and now works for Sun Microsystems.

---

### Post by RandomKillsTime on 2009-01-16
> **capscrew said:**
> Linux is the kernel only.  Debian is a disto of Linux.  Debian only uses open source software.  Other distros (SUSE and RH) use some closed source software.

Gnome is an open source desktop solution.

Ubuntu is a Debian derivative distro using Gnome as the desktop environment.  Kubuntu is a Debian derivative distro using KDE as the desktop environment.  Xubuntu uses a lightweight X-server desktop. 

A side note to all this:  Debian stands for Deb and Ian Murdock.  Ian started the Debian project and now works for Sun Microsystems.

Thank You :mrgreen:

---

### Post by amauk on 2009-01-16
In the mid 60's, AT&T embarked on an ambitious project to create an operating system to control and automate their telephone network
This project was called Multics, and was developed by AT&T's research division, Bell Labs

(you have to understand, that before this there wasn't really any such thing as an operating system.  All computer programs were written directly to the hardware.  This made “porting” programs to different hardware extremely difficult, most times requiring a total rewrite – AT&T attempted to write a platform, on top of which programs would execute – port the platform, and all programs would work)

They developed a programming language, called B (short for Bell)
the language was designed for easy porting across hardware
and Multics was written in B

Several of the developers at Bell labs felt that the Multics project took a few wrong turns
(Multics was large, complicated and a nightmare to maintain)
so when they were finished they went about developing what they considered the “right” way to develop an operating system – they named their project Unics

B had a few shortcomings, so the language was redesigned
and called C

Unics was rewritten in C
also got a spelling change, to UNIX

UNIX was an operating system designed to be redesigned
by that, I mean it didn't try to do everything (as multics did)
instead it did the bare basics

The idea was simple, purchase a UNIX license from AT&T and you got the complete source code for UNIX – then you could customise and enhance the operating system to suit your needs
as I said, it was an operating system designed to be redesigned

It's now the 80's, and out of AT&T's licensing of unix came numerous distributions of unix, the big ones being BSD (the Berkeley Software Distribution of Unix), AIX (developed by IBM), HP-UX (developed by Hewlett Packard) and a whole host of others

The computer is fast becoming a necessary staple in every business environment, and the idea of making serious money out of operating systems is realised by software companies
due to this, a lot of companies began restricting source code level access to their operating systems in an attempt to protect their development and out-do the competition

Richard Stallman saw this move to proprietary software as a bad thing, and launched the GNU project in 1983 – mission statement, to develop a unix-like operating system that maintained the once “free” nature of software

In addition to this, the increasingly proprietary nature of unix systems bred incompatibilities that seriously hampered progress
The incompatibilities between unix systems paved the way for Windows NT to stride in and take a chunk of market share (before the early 90's, Windows was a toy used only on cheap home machines by people who couldn't afford better systems)

In 1991, Linus Torvalds started work on Linux – a unix-like operating system kernel based heavily on Minix (one of the many unix variants)
Linus realised he'd bitten off more than he could chew, as developing a kernel (let alone a complete operating system) was too much for one man, so he released his kernel online and accepted the help of others

The GNU project saw an opportunity here
They'd succeeded in creating all the userland programs needed to make an operating system, but they lacked a kernel

So the GNU project selected Linux to be their kernel, and the GNU/Linux operating system was complete

Operating systems are complex things, there is no “one size fits all”
(there's something like 3000 kernel options you need to deal with when compiling the Linux kernel, let alone any of the other necessary programs that make up an OS)
because of this, individual people building their own GNU/Linux operating system is not really feasible

So, mirroring what Unix had done many years previously, different distributions of GNU/Linux cropped up – each one catering to a different audience, each one having a different goal
The GNU General Public License (GPL) was instrumental in ensuring that these distrobutions remained open, and didn't fall into the pit of proprietary, incompatible mess that unix systems had

Many (many) distros have come and gone, but a few have stuck around
Slackware, Debian and Redhat being the 3 big ones
but again, like unix before it, there's a whole heap of distributions, each aiming for a different goal

Due to the open nature of GNU/Linux systems, if you want to create a new distro, the best thing to do is use an existing distro as a base – so you're not reinventing the wheel all the time

Ubuntu is based on Debian

---

### Post by ubuntu27 on 2009-01-16
Hey nice overview amauk! 

Where is the "Thank you" button?

---

### Post by blazemore on 2009-01-16
A simplified version would be:

Unix -> Linux -> Debian -> Ubuntu

No flames for the first step plz.

Edit: Good point actually; where's our thank you button?

---

### Post by hikaricore on 2009-01-16
Certain features of the forums have been disabled temporarily until we get things stability isues sorted out.

I believe there was a sticky about this but the thanks option is included in those disabled options.

---

### Post by utnubuuser on 2009-01-16
Hey TimeKiller --Ever heard/read the word "Wikipedia.org"  -- since you managed to post here, I'm guessing you can read?

Sorry,  I apologize. re-> -- since you managed to post here, I'm guessing you can read?

---

### Post by dcstar on 2009-01-16
> **amauk said:**
> 
........
In addition to this, the increasingly proprietary nature of unix systems bred incompatibilities that seriously hampered progress
The incompatibilities between unix systems paved the way for Windows NT to stride in and take a chunk of market share (before the early 90's, Windows was a toy used only on cheap home machines by people who couldn't afford better systems)
.......

Well, at the risk of being off-topic let's have a slightly different opinion here:

Back in the early 90's "ordinary" people wanted networking, and when Novell got complacent with their NetWare product that opened the door for Microsoft to get into the server market as well as the desktop.

There was never any market back then that saw Unix replaced by a Microsoft product, they were in almost different domains (no pun intended) and the growing business market for LAN based networks saw Microsoft take off with their superior (and affordable) desktop/server integration.

Unix was a great platform for dedicated applications (and affordable if you used something like SCO Unix on "standard" Intel hardware) back then but it was only the top-end users that seemed to use Unix for their network solutions.

Once the Internet/long distance networking became accessible (and affordable) for businesses one company had a big installed base to add on all of the network services taken for granted today (web site, e-mail etc) and were able to provide them without their customers having to deal with that arcane Unix-thingy technology....... and so it began.....


PS I still remember installing SCO Unix using 45+ floppy disks (before CD-ROMS became common) feeding them in one at a time........ imagine doing that on 4 or 5 servers in a row....... but it was better than using Windows 3.11!

---

### Post by hikaricore on 2009-01-16
> **utnubuuser said:**
> Hey TimeKiller --Ever heard/read the word "Wikipedia.org"  -- since you managed to post here, I'm guessing you can read?

That is not appropriate.

If you don't have anything constructive to add to the conversation please don't post in it.

---

### Post by amauk on 2009-01-16
@ dcstar

I left out a whole heap of stuff (including networking) just to keep it as short as possible

one of the biggest incompatibilities between different unix variants was indeed networking (there were half-a-dozen different protocols, with BSD's TCP/IP being but one)

but you're right
it was the integration that Windows offered that made it attractive

that, and there was a whole generation of people who were brought up on MS-DOS at home, because it ran on cheap hardware - Windows was a natural choice for these people

Better the devil you know, and all that

---

### Post by RandomKillsTime on 2009-01-16
Thanks amauk and all the other posters.

---

### Post by delete happy on 2009-01-16
Thanks amauk and dcstar! I've been wondering the same thing. Its not lazyness to want a condensed version, but sometimes it good to get the big picture. It kinda gives me an idea where to start looking for further questions.

---

### Post by emigrant on 2009-11-20
thanks [amauk]("http://ubuntuforums.org/member.php?u=384906") :)

---

