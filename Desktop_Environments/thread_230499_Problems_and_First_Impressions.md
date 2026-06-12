---
title: "Problems and First Impressions"
date: 2006-08-06
forum: Desktop Environments
---

### Post by zambizzi on 2006-08-06
I've been using Gentoo faithfully for almost three years now and while I love it and will continue to use it as a server OS - I needed to find a more "stable" linux desktop that changes far less often.

I'm giving Ubuntu a serious shot and so far I'm (mostly) very pleased...it certainly lives up to its reputation!  I'm particularly impressed because it loaded *all* of my hardware flawlessly.  Why is that a big deal?  I have a Toshiba Satellite 5205-S503 laptop...'nuff said.

Enough of the praise, here's the issues I've had so far.  :) 

1. Kernel - I upgraded to the 686 kernel and while it *did* boot, I found that I could not install a lot of software through the add/remove tool.  I repeatedly got errors that my "architecture is not supported" (paraphrasing, it was something like that.)  I'm not sure why a Pentium 4 would be unsupported w/ a 686 kernel but supported w/ a 386 kernel so I'll guess it's a bug.  Bummer, would like the faster kernel, obviously.

2. CPU is busy - Upon booting up my CPU runs between 5% - 9% w/ nothing but the default startup apps.  I even disabled the cron daemons, print services, and one of the logging services.  Upon running 'top' it looks like Xorg is the culprit.  Any way to calm it down?  I'm not running XGL and I'm using the 7174 "legacy" nvidia drivers (the 8xxx make the PC freeze up entirely...did this on Gentoo too.)

Any help/suggestions are much appreciated!  Thanks!

---

### Post by zambizzi on 2006-08-08
I'm sorry...is there any chance of getting some help here?

I'm stuck w/ a 386 kernel and can't install *critical* applications when I upgrade to the 686...I *can't* be the first one to experience this - I've had this problem on two different machines now.  I'm not interested in learning automatix right now (unless this is the official work-around.)

My CPU is constantly being sucked up at around 9% - this just shouldn't be...is there something I can do here?

Any help/suggestions would be greatly appreciated...thanks! :)

---

### Post by vtel57 on 2006-08-08
I can't help you, but I'll bump this thread for you. 

Luck!

~Eric

---

### Post by zambizzi on 2006-08-08
I appreciate that!

I actually worked around some of these issues.  I found the ubuntu wiki post-install guide and replaced all of my repos w/ the suggested list...and while I get an error about "duplicates" in the list, the stuff I needed actually installs

It's a shame that this isn't configured correctly by default, the real greenhorns switching over from Windows or MacOS must go mad trying to get the software they want when first using Ubuntu.

Anyhow, I got the 686 kernel installed and re-installed the nvidia drivers before rebooting and luckily, I didn't get nuked on my display...real happy there.  It seems a bit snappier but my proc is still pegged at 9% most of the time - not real happy 'bout that....oh well...I'll get there eventually.

Thanks anyhow!

---

### Post by vtel57 on 2006-08-08
Heh! I AM a greenhorn, but I can tell you about one thing that really worked well for me...

[SIZE="6"]AUTOMATIX![/SIZE] :)

---

### Post by zambizzi on 2006-08-08
I'm not a linux greenhorn, I've been using it on the desktop for years now...the server a little longer.

My comment was really just an observation...I'm sure automatix is great for new users...but how much effort would it have really taken to put the right repos in place to begin with.  And, if that wasn't a possibility, install automatix by default?

I'd rather not use Automatix, I *do* want to learn the guts of the distro if I decide to stick it out.

You can take the boy out of Gentoo but you can't take the Gentoo out of the boy. ;)

---

### Post by vtel57 on 2006-08-09
Oh, I whole-heartedly agree with your thoughts on "learning the guts". I've been on a steep learning curve with Ubuntu 6.06 for the past 3 or 4 weeks now. I've come a long way (with some help from friends and a pile of good Linux books) in that short time. I'm no computer dummy, I was programming 8080s back in the late 70s, but haven't done any real under the hood stuff since I became a Windows zombie for the past 6 or 7 years. This is my first real experience with GNU/Linux. I'm having a blast! I should have gotten involved with this OS years ago.

Regards, 

~Eric

---

### Post by zambizzi on 2006-08-09
Heck man, you may even want to try Gentoo once you've gotten broken in a little (ha!).  IMO, it's a Linux rite-of-passage.  It's an excellent and extremely powerful distro but you've got to have the time and patience.  These days, working around the clock, I've got neither - which is why I'm taking a stab at Ubuntu as a possible replacement.  The Debian roots give it instant street-cred.

Anyhow, Linux is definitely worth it...you won't be sorry for the time you're investing.

Now, if I could only convince my hard-core Windows-zombie boss of the same thing. :cool:

---

### Post by vtel57 on 2006-08-09
Yeah, I've got CDs of Debian Sarge, PCLinuxOS, and Fedora Core sitting in front of me right now. I'll definitely being experimenting once I get a little more comfortable with it. I'll probably throw together a "guinea pig" system from an old Athlon XP 2400+ box that I have sitting around here. Either that or I'm going to use that box with 4 200Gig Seagates in RAID as a LAN LinServer here in my house. ;)

---

