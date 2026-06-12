---
title: "Problem with nautilus cd/dvd burning"
date: 2005-03-22
forum: Desktop Environments
---

### Post by guyer on 2005-03-22
Ok, so I've been struggling with this problem for a few weeks now off and on...  There are 3 Ubuntu users in the office (all warty).  Two of us are having the same problem.  After a fresh install, cd/dvd burning doesn't work.  Everything seems fine... I have two drives, both are detected and I can read from them.  First, when I pop in a blank cd or dvd, nothing happens.  When I open burn:/// and drag files in to burn, everything seems fine but when burning is about to start (after the image is created), I get "Reload rewritable or blank media".  Both drives exhibit the same behavior.  

I dual boot to WinXP and both drives work in that env.  In Ubuntu though, I can burn a cd on both devices using `cdrecord dev=/dev/hdc backup.tar.gz` but then the cd isn't readable.  Does anyone have any thoughts?

Output from dmesg and lsmod is attached.

---

### Post by burlap on 2005-03-22
Is it cd-r or cd-rw you are trying to burn? 

If this is cd-rw, see for example [this](http://www.ubuntuforums.org/showthread.php?t=20765) or [this](http://www.ubuntuforums.org/showthread.php?t=18304).

---

### Post by guyer on 2005-03-22
All cd-r.  I almost never use rw functionality as I'm typically just archiving.

---

### Post by burlap on 2005-03-22
No ideas then. Fortunatelly for me cd-r burning works fine (I'm also usually archiving, once the only cd I got was a cd-rw... But anyway I'm trying to entangle this as I would like to have every functionality, even if hardly used...). 

You can try some more "verbose" frontends to cdrecord (gnome-baker which is nice gnome-integrated, xcdroast which is old-school but reliable, or graveman - also gnomish) and there you can look at the output. On the other hand you can experiment with options in CLI yourself... 

Good luck!

---

### Post by brousch on 2005-03-22
When I had very similar problems to yours it was due to crappy CD-R media. The media worked fine for a few months but degraded to non-usability. I confirmed this was the problem by trying 2 different CD writers through ubuntu and windows on 2 different computers.

I bought some higher-quality media and now it works fine again.

I learned my lesson: stick to the name brands!

---

### Post by guyer on 2005-03-22
I have tried GnomeBaker which works but only for cd's.  I really need to use both...  I've looked into cdrecord-ProDVD but device support appears sketchy.  I'm a little hazy on how nautilus-cd-burner supports dvd burning anyway...  Hmm...  what's disturbing is that I think that if I could get nautilus-cd-burner to recognize that there's a valid blank disk in the drive, it would work.  Any ideas on how I could find out what's happening to cause it to not find the media?  Where does it log to?  I've looked all over.

---

### Post by brousch on 2005-03-22
If skanky media is the problem, using other CD burning programs will do you no good. I recommend you get a high quality, blank CD-R and try to burn to it.

I had exactly your types of problems. Media was not being recognized, or, if it was, the burn would fail within seconds even at 4x.

---

### Post by guyer on 2005-03-22
Sorry, brousch, I didn't reply to you earlier...  I don't think media is the problem.  I can burn a cd successfully using GnomeBaker.  The media is made by Phillips which I consider to be a reputable company...  I've also tried a new Memorex CDRW.  Same behavior.

---

