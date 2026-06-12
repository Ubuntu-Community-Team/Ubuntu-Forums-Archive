---
title: "Screensaver Blanks Too Soon"
date: 2007-11-10
forum: Desktop Environments
---

### Post by PaulMasters on 2007-11-10
Been a Windows user since the 3.1 days, and I've only been using Ubuntu for a few weeks - and the more I use it, the more I like it.  I'm running Ubuntu Gutsy (7.10) with Gnome 2.20.0 on a home-built desktop, dual-booted (via Wubi) with Win XP.

Trying to get screensaver to behave properly.  It starts at the appointed time, but blanks after 10 minutes or so (haven't really timed it) even with Power Management settings at Never.

I have compiz installed and running; all screensavers are present and do, in fact, play.  They just go to a blank screen too soon.

I've rummaged through some related threads, but no answer seems to apply to my situation.

Thanks in advance...

---

### Post by LaDeuce on 2007-11-12
I've got no solution to offer.  Just wanted to post and say that you are not alone.  I've noticed that since installing compiz my screen also blanks early.

I start with a blanked screen, move the mouse then view a glimpse of my screen saver before being presented with the login screen to unlock the terminal.

E

---

### Post by seachnasaigh on 2007-11-12
I've noticed this behaviour too, though I'm not sure it's an Ubuntu problem so much perhaps as a Gnome problem. The reason I say this is that I've experienced the same behaviour under Fedora Core (2-6) and RedHat (7.1 - current Enterprise) all using Gnome as a desktop. I haven't seen the same problem under KDE (then again, I don't use KDE often enough to consider myself an expert) and it's always irritated me. If I wanted a blank screen, I would have set it to that. If I want a matrix screen and uncheck the blank screen box, I expect the OS to behave and do that. I'll be very interested if someone has a fix for this. You're not alone, and it's not new. Again, I'm just not sure it's an Ubuntu problem.

---

### Post by magiceraser06 on 2007-11-14
I just wanted to through in my two cents into the pot.  I too suffer from this problem. It seems to be more a Gutsy thing, as Feisty never did it.  

Its the worst when playing movies.  I have to constantly keep the mouse moving or it will blank out while playing the movie.  Very frustrating.

I installed xscreensaver to no avail.  removing didn't fix it either.  

so, if its a common problem, are there any bug reports on it?  anybody come with a fix yet?

keep up the work guys.

thanks.

---

### Post by jkooebye on 2007-11-14
Greetings, 

I too am having the same problem. I find it very frustrating like said before during movies. I have a couch and I watch my movies from there. Every 15 minutes or so i have to get up to move the mouse. Not sure how to fix it but it would be nice if someone looked into it. Thanks

Joe

---

### Post by magiceraser06 on 2007-11-14
Hey guys.  I found this fix the forums.  Seems to work for many, but others not.  I will post my results once I get home to test it.

But here is the skinny, many thanks to:  jocko for finding a solution (possibly)

You'll have to edit your /etc/X11/xorg.conf file.

```

sudo gedit /etc/X11/xorg.conf

```

Then add these lines to the very end of the file

```

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

```

Hope that helps some.  Sure hope it helps me too.

EDIT:
YESSSSSS!!    It freakin works.  Hope that will help all the rest of you out there.  im loving it!!

---

### Post by seachnasaigh on 2007-11-15
NICE work magiceraser06. I tried that on both the Ubuntu laptop and a Fedora desktop ... file's in a slightly different place, but the fix works just fine. Thanks for digging on that! 

Side note: I rebooted both of them after making the change. I probably could've also done [sudo /etc/init.d/xinetd restart] on Ubuntu or [# /etc/rc.d/init.d/xinetd restart] on Fedora and achieved the same thing ... either way, you have to get it to re-read the conf file I think.

ckr

---

### Post by magiceraser06 on 2007-11-18
Actually in Ubuntu you only need to type into Terminal:

```

sudo shutdown -r now

```

That will completely restart your computer.  One could also just do a CTRL+F2 to end the GDM and start up in the command prompt at which point, one can type:

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

at which point you should load back into Gnome and enter your password as normal.  

Hope that helps.

---

