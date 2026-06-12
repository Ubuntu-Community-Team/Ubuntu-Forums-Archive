---
title: "Nothing in App/Places/System opens anymore?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by xyz on 2006-06-08
Hi-
Well, I wonder what I did to get to where I am now but I just don't know!
-unable to open a terminal, text editor or anything else for that matter
-can't "Add to Panel"
-trying to run Synaptic, Iget:
> Failed to run /usr/sbin/synaptic as user root: unable to copy the user's Xauthorization file
How bad is it, Doc?
Should I provide more info for you to help?

---

### Post by nanotube on 2006-06-08
[QUOTE=xyz]Hi-
Well, I wonder what I did to get to where I am now but I just don't know!
-unable to open a terminal, text editor or anything else for that matter
-can't "Add to Panel"
-trying to run Synaptic, Iget:

How bad is it, Doc?
Should I provide more info for you to help?[/QUOTE]
hmm, well, this error seems to have very little info about it. let's look around.

can you go to another console (hit Ctrl-Alt-F2), log in, and check the permissions on your .Xauthority file (as in, run command "ls -al .Xauthority" and post the output here.

and, can you think of anything you did before this started happening?
have you tried rebooting?

---

### Post by xyz on 2006-06-08
I've been trying to upgrade (via internet) but have so far reinstalled Breezy 3 times. It turned out I had basic pbms within Breezy as I kept getting stuff like:
> Archives is too short
E: Prior errors apply to /var/cache/apt/archives-linux-images....deb
As root I deleted a bunch of .deb,linux-restricted and sudo apt-get updated Breezy fine.
Booting I noticed a few lines I wanted to try to solve and understand what the heck they were doing there:
> 1. Setting LVM Volume Group5
Error 16 inconsistent filesystem structure

2.hda:drive ready for command
This took,say,quite some time and that's why I'm having a hard time recalling everything I did before this started happenning. It is, however, related to 1. or 2. problems.
I remember visiting some German site dealing with one of the issues. I seem to recall it advised to disable Stage1 and Stage2!! which I believe I must've done! Does this ring a bell?
**Having no terminal access**, I did a Ctrl+Alt+F1 to get one. Tried running sudo and got:
> can't open /var/run/sudo/user/tty1 read only file 
And then my finger pressing hard on the power button did nothing to shut down my box. Had to pull the plug off my laptop!

I realize this is a mess of an explanation and I'm sorry about that. I do need a working OS real soon so I may have to reinstall within the next couple of hours at the latest (it is nearly 5 AM my time now). However, I'd like to understand what happened, why access to App/Places/System aborted, how to get a terminal when there's none and even Ctrl+Alt+F1..2...3...doesn't work as an alternative tty because of a /var/run/sudo/user/tty problem.

Rebooting did nothing good; recovery mode no longer worked.

nanotube, thanks for having paid attention to my problem.8-)

---

### Post by nanotube on 2006-06-09
[QUOTE=xyz]I've been trying to upgrade (via internet) but have so far reinstalled Breezy 3 times. It turned out I had basic pbms within Breezy as I kept getting stuff like:

As root I deleted a bunch of .deb,linux-restricted and sudo apt-get updated Breezy fine.
Booting I noticed a few lines I wanted to try to solve and understand what the heck they were doing there:

This took,say,quite some time and that's why I'm having a hard time recalling everything I did before this started happenning. It is, however, related to 1. or 2. problems.
I remember visiting some German site dealing with one of the issues. I seem to recall it advised to disable Stage1 and Stage2!! which I believe I must've done! Does this ring a bell?
**Having no terminal access**, I did a Ctrl+Alt+F1 to get one. Tried running sudo and got:
 
And then my finger pressing hard on the power button did nothing to shut down my box. Had to pull the plug off my laptop!

I realize this is a mess of an explanation and I'm sorry about that. I do need a working OS real soon so I may have to reinstall within the next couple of hours at the latest (it is nearly 5 AM my time now). However, I'd like to understand what happened, why access to App/Places/System aborted, how to get a terminal when there's none and even Ctrl+Alt+F1..2...3...doesn't work as an alternative tty because of a /var/run/sudo/user/tty problem.

Rebooting did nothing good; recovery mode no longer worked.

nanotube, thanks for having paid attention to my problem.8-)[/QUOTE]

wow, heh well... it looks like a reinstall is your best bet at this point. why don't you back up all your data (you can boot to a livecd, mount your drive, and burn your data to cd or something), and then do a fresh install of dapper? at least that would solve your problems trying to upgrade to dapper. :)

---

### Post by xyz on 2006-06-09
Yes reinstalling is the only way to go! Prior to fresh-installing Dapper, I need to get an 80-minute CD because it 'weighs' 70**8**MB! In the meantime, I'll use Breezy til Monday.
Have a good weekend and thanks again for the support.

---

### Post by nanotube on 2006-06-09
[QUOTE=xyz]Yes reinstalling is the only way to go! Prior to fresh-installing Dapper, I need to get an 80-minute CD because it 'weighs' 70**8**MB! In the meantime, I'll use Breezy til Monday.
Have a good weekend and thanks again for the support.[/QUOTE]
hmm, i recently downloaded the dapper release, and it was only 697.8 mb. so you can get off with a regular 700meg cd. i don't know where you got the 708m size :)

well, good luck ;)

---

### Post by xyz on 2006-06-10
Well, I thought I'd read somewhere that,for some reason, we had to download ubuntu-6.06-**alternate**-i386.iso which amounts to 708.9 MB but I'm obviouly mistaken!
The regular download does stand right under 700 MB. Thanks for letting me know. I'll go and get it.

EDIT:
I went here:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)
Click on Desktop CD
1.PC (Intel x86 desktop CD = 714.6MB
2. Server Install CD
PC (INtel x86) server install CD = 442MB
3.Alternate install CD
PC (Intel x86) alternate install CD = 708.9MB

Reading what you wrote about it, I must admit I'm a bit confused. I normally download #1 in my list and it works fine.
Is this the one I should download:
> ubuntu-6.06-alternate-i386.iso            30-May-2006 22:06  692M  Alternate install CD for PC (Intel x86) computers (standard download)

and in that case, what "more" would I get downloading #1 or # 3?

EDIT 2:
EDIT 2:
Following the mirror link I gave above, I do see that all install CD for PC (intel x86) downloads read 692M or 698M; however, when I click to download they all read over 700M!!

I'm missing something here.

---

### Post by nanotube on 2006-06-10
to make a fresh install of dapper, this is the one you should download
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso)

it is 698 megs. the different numbers you get are probably due to 714XXX kb = 697 megs (because we divide by 1024, not by 1000)

have fun :)

---

### Post by xyz on 2006-06-12
Hey thanks for explaining this. I-m downloading right now!
Clicking to download does indicate 714.6 but I had forgotten about the 1024 division!!
My brain must be "divided" too!

---

### Post by nanotube on 2006-06-12
[QUOTE=xyz]Hey thanks for explaining this. I-m downloading right now!
Clicking to download does indicate 714.6 but I had forgotten about the 1024 division!!
My brain must be "divided" too![/QUOTE]
hehe :)

---

