---
title: "Why Ubuntu?"
date: 2004-10-18
forum: General Help
---

### Post by retiefdv on 2004-10-18
I am a complete Linux Newbie - having "grown up" in the Windows world. I have never used the Linux command line and would like to stay away from the command line, if at all possible. That's what GUI's are for!

I do feel the OSS movement is something I must get involved in. On my new home computer I partitioned the hard drive into two 40Gb partitions and installed WinXP on the one partition and Mandrake Linux on the other.

The OSS is getting more momentum here in South Africa as a result of the efforts of the Shuttleworth foundation. The Ubuntu Linux distro is one of the results of this effort.

Is there a compelling, non-emotional, reason why I must swop out Mandrake and install Ubuntu Linux? If so, then how must I go about doing this, given my current hard drive partitions?

---

### Post by LongTooth on 2004-10-18
Can't help but get emotional but I'll try not to. Forget the business practices of MS and look at the security issues only. Aren't you tired of have to fight virii, worms, trojans, pop-ups and...well, you get the idea. Windows would be a great OS of it wasn't for these glaring faults  and the fact they won't allow you any choice. As Linux grows there will come a time when Linux users will have to address the problem of virii but hopefully not anytime soon. And I believe that problem will be handled alot better that MS does. 

As far a a distro, pick one that appeals to you and stick to it. Debian has always had a reputation for being diffucult to install but with Ubuntu and other like it (Mepis, Knoppix to name two) that is not an issue any longer. This is my first forray into the debian world and I'm liking it.  

Started out with Mandrake years ago. Nothing wrong with it. It has a great following and I'd put it up against any other. It's a matter of tastes and choice. At the moment I'm using Fedora Core 2 as my main distro and running Ubuntu on my test box. Jump into the linux waters, I think you'll find it to your liking. What I like about Ubuntu is the programs first installed. Unlike most distros, you have what you need. Not several of the same programs which only confuse a newbie like yourself. Once you get your feet wet and have an idea of what's going on, you have the choice to install another program more to your liking. It's about choice.

Command Line: It's not that bad. Really. I use it about half the time. And there are plenty of GUIs for you to use if the CLI is not to your liking. Choice. It's there in Linux.

---

### Post by cseg on 2004-10-18
[quote=retiefdv]I have never used the Linux command line and would like to stay away from the command line, if at all possible. That's what GUI's are for![/quote]After I had been using computers for 10 years using 2-figured typing, I finally took a typing class through the local adult education program.  I really wish I had taken typing in high school, but it was not the cool thing to do.  But I finally broke down and took a typing class on my own because I knew it would make me a more efficient computer user, both on the command line and not.

Is it the inability to type which scares people away from the command line?  The first thing I do on any Windows box I have to use is install Cygwin, so that I have a sensible (and powerful) command line environment.  

For example, my team manages a fair number of testing environments that have application servers which occasionally go down.  For me to restart a particular application server, I type:

   restart app_server_name

Other people on my team have to:
   1) figure out which host this app server is on
   2) figure out whether to use VNC, Windows Remote Desktop or VMWare Remote Console for that host
   3) click around the host via a (slow) remote visual tool until you find the right directory for that app server
   4) click on stop-app-server (to make sure its down cleanly)
   5) click on start-app-server

I have all this scripted so that I can issue a single simple command.  This is the power of the command line and it is really too bad that more people have not mastered it...and that Windows users are afraid of it.

---

### Post by cseg on 2004-10-18
[quote=retiefdv]Is there a compelling, non-emotional, reason why I must swop out Mandrake and install Ubuntu Linux? If so, then how must I go about doing this, given my current hard drive partitions?[/quote]As far as why, I'm not sure I can answer that.  It has very recent versions of software (kernel, Gnome, etc), it's base on Debian (yay!).  I guess it depends on whether you have any work that would be lost by overwriting Mandrake (which is one reason to put /home on a separate partition).

If you want to go ahead with this, its fairly easy.  Burn the ISO, boot to it, choose your old Mandrake partition as your installation partition, finish installation.  You will boot to a new Ubuntu system where your Mandrake system used to be.

Of course, your other choice is to triple boot.  This would require down-sizing your Mandrake partition to make room.  You could do this with QT-Part (?) which you can use by booting to a Knoppix CD.  Once you have shrunk your Mandrake partion and have some free partition space (Ubuntu can be installed with less than 5 Gig), boot to your Ubuntu install CD and install to that new (empty) partition.

And if you're going to go this far, you might as well put /home on its own partition (as mentioned above).  That way you won't lose any of your local work when you re-install Linux.

---

### Post by FLeiXiuS on 2004-10-18
With your current condition I would recommend completely re-installing the / directory.  If your not to sure of what this means, boot the Ubuntu Warty ISO and complete the installation with Auto Paritioning.

Unfortanately its impossible to learn linux the correct way without going through CLI (Commind Line Interface).  I would prefer all Linux Basic users to begin in the CLI facinities.

You will see that with the currently GUI abilities you a greater deal of control over your system if you use Command Line.  Learn to use it and live to love it as I say.  

Now back a conclusion...

Follow all instructions into the partitioning manager in the Ubuntu Install.  Its very follow through.  If you have completed the Mandrake install, this should be just as easy!  Have fun and remember to love your Ubuntu! :D

---

### Post by im_ka on 2004-10-18
it took me about 6 months to get a solid linux knowledge, and i do have a life (study, girlfriend, work, friends, etc.).
i've been using linux since december last year, and now i can say that i've found the distro that fits my needs.

i think it's inevitable for newbies to check out different distros, and the best way to learn is to go through "cli intensive" (arch, slackware, debian, gentoo... or even linux from scratch) ones. maybe you'll fall in love with some "do it yourself distribution", or rely on fancy gui's (anaconda, yast). maybe you'll like something in the middle, like i do.

you may start with ubuntu, you probably move on (because you're curious and wanna learn), you might end up using ubuntu again.

it can not be said/written enough times: unix is about choices

---

