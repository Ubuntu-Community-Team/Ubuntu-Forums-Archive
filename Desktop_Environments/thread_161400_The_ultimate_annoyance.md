---
title: "The ultimate annoyance"
date: 2006-04-17
forum: Desktop Environments
---

### Post by link141 on 2006-04-17
(I just spent the past hour writing this, so please respond to it) Keep in mind that I know absolutely nothing about linux.
I've just installed Kubuntu on my computer two days ago.  My computer is a "home built" computer consisting of other parts from computers I no longer own, a store bought proccessor, and a store bought mother board.  My proccessor is a Pentium 4 3.0 GHz with HT, and my mother board is of the ASUS-P4 series, if it helps.  I've faced some problems with it in general though that frustrate me deeply.  I'll put them in a list to make it easier to read:

1. I've had trouble with the automatic partitioner setting up a partition on the same hard drive windows is on. It starts out fine then gives me an error message saying that that there isn't enough space in that on the drive when I've only used 20 GBs of an 80gb hard drive, and tells me to manually reformat the hard drive (which I have no idea how to do and my dad tells me it's a nightmare). Obviosly, to have Kubuntu installed, I put in a six year old, 10gb hard drive in the box and put it on that.  I want to have it on the same drive for sake of space, and know what to do when confronted with the same message on my other computer with a 250 gb SETA drive.  If you know an easy way to do this without messing up the hard drive, could you let me know?  

2.  When I try to execute an exe file by double clicking on it in Konquer, absolutely nothing happens.  When I right click it and select open in new window it asks me if I'm sure I want to execute it, the same.  I tried it in nautlis, and again nothing happened. This is dissapointing because the repositoiry version of this program is not up to date, and on the site I strictly followed the install instructions, specific for KDE and Gnome, and it told me just to double click on it.  Double clicking the exe file for  LMMS worked perfectly.  Does this mean that the versions of the programs you want are strictly limited to the out-dated versions in the repositoiries.  I don't want to learn how to program linux just to install up-to-date software.

3.  I've been having problems with the alsa sound driver.  The problem: it's not there!  This frustrates me because it is apparently the default sound driver for many sound based programs.  When I tried to look it up in adept, I found many programs and components centered around this driver, but not the actual driver.  My guess is that the CD I installed it with had a corrupted version of this driver, I've already had a case where the install CD was corrupted from one site.  Yet, the fact that the same thing happened on the ubuntu live CD disproves this theory.  In some applications you can't change the sound driver, and it will make the most annoying sound of shattering glass when the error message pops up: no useable sound driver found. How did it make that sound if this is true? If this is a problem others have experienced, and are there any solution.

These are more like questions than actual problems:
1.  How can you change boot sequence of grub? 

2.  How can you read the files of other computers over the network (assuming you can)

3.  I am planning to purchase an Nvidia graphics card and possibly other extensions for my computer.  I am pleased to hear that my first preference of graphics card is compatible with linux systems but I want to know if Kubuntu will detect it and fetch a driver for it or what.  Will this be true for all new hardware.

4.  Whenever a program crashes or locks up, is there an easy way to call up the system moniter, jump to the process and kill it. 

5.  What is Katapult?  It looks like to me a hot-key program launcher.  If so than how can I use it.

6.  This relates to problem 2.  How can you install downloaded programs from their tar balls, or any other files?

This is probably only a small number of problems I've faced so far, It's late and I'm sick with something nasty, probably mono.  Someone, anyone, PLEASE HELP!   I don't want to go back to relying soley upon Windows [COLOR="SeaGreen"]X[/COLOR]tra [COLOR="SeaGreen"]P[/COLOR]utrid, It's a peice of (sensored for overly fond feelings).  If anyone has the solutions to at least some of these problems, please inform me.  A HUGE thank you to anyone who helps.
My feelings right now: ](*,)x5

---

### Post by gerbman on 2006-04-17
Hey there. Don't fret too much yet, tons of experienced users on this forum to help out.

> I've had trouble with the automatic partitioner setting up a partition on the same hard drive windows is on. It starts out fine then gives me an error message saying that that there isn't enough space in that on the drive when I've only used 20 GBs of an 80gb hard drive, and tells me to manually reformat the hard drive (which I have no idea how to do and my dad tells me it's a nightmare).The easiest method I've used is to free up space at the end of the drive before running the installer, and install Ubuntu to partitions created in that free space. This can be done with GParted on the LiveCD in most cases. If you have questions about GParted just ask.

> When I try to execute an exe file by double clicking on it in Konquer, absolutely nothing happens.  When I right click it and select open in new window it asks me if I'm sure I want to execute it, the same.  I tried it in nautlis, and again nothing happened.What application are you trying to run? Open up a terminal window with Applications->Accessories->Terminal. Type the command to start the program into the terminal and see what output/error messages you get, if any. You might have to change the directory to where the executable is located before.

> Does this mean that the versions of the programs you want are strictly limited to the out-dated versions in the repositoiries.It's generally much easier to install programs from the repositories. But in the case where you must have the most current version you can usually get the program compiled from source code.

> How can you change boot sequence of grub?I think you can edit /boot/grub/menu.lst to do this. At the bottom the different boot options are listed. I think you can just change their order. Look into this first, as I don't want to be responsible for an un-bootable system ;-)

> I am pleased to hear that my first preference of graphics card is compatible with linux systems but I want to know if Kubuntu will detect it and fetch a driver for it or what.You'll have to install the driver, I think, but it's not difficult. I'm sure there is a tutorial on this forum (I have an ATI card, so I don't know for sure).

> Will this be true for all new hardware.
Nope. Some hardware is quite unsupported, but it's getting better all the time and it's quite good now.

> Whenever a program crashes or locks up, is there an easy way to call up the system moniter, jump to the process and kill it.Yes. Open up a terminal again, and type```
ps -e
```to list all currently running processes. The number along the left side is the process ID. Type```
kill <PID>
```to kill the process, where <PID> is the process ID. Type "top" to see a list of processes consuming the most CPU cycles. You can also type```
pkill <application>
```to kill an application named <application>

> This relates to problem 2.  How can you install downloaded programs from their tar balls, or any other files?This usually involves compiling the source code. There is typically a README file in the programs folder that tells you the procedure for compilation.

My answers were short, but only because I have confidence in you :-) Post any questions you have and someone will try to help.

---

### Post by aysiu on 2006-04-17
You may find these links helpful:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by link141 on 2006-04-17
Thank you! You are the first person to answer a post that I've made, and at midnight too!  Now I know how to end evil and diabolical processes!  That will help in the future.  I'll probably make some more posts tommorrow about any problems I have.  Quick question: How much do you dislike windows?

---

### Post by gerbman on 2006-04-17
[QUOTE=link141]Thank you! You are the first person to answer a post that I've made, and at midnight too![/QUOTE]This forum rocks :-D

> Quick question: How much do you dislike windows?I don't dislike it, I just don't prefer it as my primary OS. I think you'll find that the experienced Linux users (not saying I am one) believe Windows is a good OS for some people but not for others. It's totally what fits the user, and for some users it doesn't get any better than Windows. I just don't feel empowered by Windows to do what I want with the system. In that respect Windows sucks, but only from my perspective. Windows is a good OS, that should be obvious.

---

### Post by gerbman on 2006-04-17
You can also go to Applications->System Tools->System Monitor to inspect/kill processes. The keyboard is sooo much more fun though :-)

---

### Post by link141 on 2006-04-17
No offense but windows is full of bugs, a hodge-podge of incoherent code purchased from third-party companies that had no original intention of thier code appearing it.  It's inefficient, sloppy, poorly programed, and space hungry.  To prove this open task manager and see what the hungriest process is... It's system idol process.  Thats the millions of cycles of usesless code windows has running from as a result of how badly programmed it is.  That was my main reason for going linux!  On top of all that, it's four times the price of *good* software.  I'm not trying to start a fight, just open your eyes to what windows really is.

---

### Post by gerbman on 2006-04-17
[QUOTE=link141]To prove this open task manager and see what the hungriest process is... It's system idol process.  Thats the millions of cycles of usesless code windows has running from as a result of how badly programmed it is.[/QUOTE]When the system idle process is taking up "99%" of the cycles, that doesn't mean other processes don't have access to them. All it means is that all the processes on the system (combined) don't require more than 1% of the CPU time. If the system idle process was always at 99% that would imply Windows is a very efficient OS.

---

### Post by pranav on 2006-04-17
As you are new to Linux, I'd suggest you try out other distros of GNU/Linux as well.

I love Ubuntu(Debian-based) and 6 months back Ubuntu was the 1st distro I tried. Ubuntu has a very sound philosophy and the best forum.

However, a Windows user when comes to GNU/Linux in general and not any one distro in particular I would suggest that you should try out some other interesting distros to truly understand how powerful, diverse, interesting and useful GNU/Linux really is.

I have Knoppix 4, Mandriva 2006, Mepis 3.4-4 and Ubuntu Dapper installed. Annoying XPerience crashed & havent bothered reinstalling it.

Try Live CDs of other distros that interest you. GNU/Linux is a matter of choice, you can make a choice when you know what the options are. So get to know your options and test-drive them thru thier Live CDs. [www.distrowatch.com]("http://www.distrowatch.com/") should give you a lot of choices

You have a very good PC with a lot of power. XP will never be able to do justice and utilize that power, GNU/Linux can.

All the same you shud try out a distro that will make everything work out of the box for you. Knoppix (Debian-based) and Mepis (which is going to be Ubuntu-based from now on) are interesting options. These are Live CDs which can be installed if you like. 

Dont get me wrong Ubuntu can also handle everything that these distros do, but due to legal issues(not technical issues), Ubuntu doesnt come bundled with all the plugins, codecs, etc. You need to install them and that is what scares away most people due to various reasons(lack of an internet connection is one of the larger reasons in my country India where internet is a luxury).

Who knows in a year from now you could actually be remastering your own distro with the positives extracted from several distros rolled into one. 

This is what GNU/Linux is about. Choice & customization rather than accepting the limited options (if any) that Microsoft gives you. It doesnt give you but instead takes money from you. Here its friends from across the world holding your hand and helping you learn and grow.

Welcome to GNU/LINUX :)

---

### Post by tribaal on 2006-04-17
If the unused computer cycles annoy you so much (just like they annoy me), you should maybe consider joining a distributed computing project, such as [rosetta@home]("http://boinc.bakerlab.org/rosetta/") :)

This will put the idle cycles to work on proteins folding, something that will help scientists find cures for diseases, but the priority is set to be the lowest possible, so that means your applications will not "freeze" or slow down because of it...

There's help on the installation process [here]("http://wiki.debian.org/BOINC#Installation") if you're interested.

- trib'

---

