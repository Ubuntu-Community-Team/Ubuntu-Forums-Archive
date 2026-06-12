---
title: "OpenOffice Impress performance issues"
date: 2007-05-17
forum: Desktop Environments
---

### Post by crab on 2007-05-17
Hi All

I'm a new convert to Ubuntu running a dual boot  Win XP and FiestyFawn 7.04 on a sony Viao VGN laptop.

The only issue i have had so far, is with OpenOffice Impress: A slideshow authored in Impress with about ten slides runs extremely slowly - about a four second delay between slides - this is with text only slides, no graphics files, no transitions, no other applications running.

I've fiddled with application memory allocation but it seems to have no effect.

Is this a known issue? Is there something i am missing? or is there a work around to speed up performance?

many thanks

crab

---

### Post by glockster on 2007-06-26
I am creating a presentation in Impress also.  I have a Dell D820 with 2 GB Ram and Duo Core 2 processor.  Fresh install.  Creating the process was real sluggish.  Now I was importing pics from a SMB share.  But once I saved it was still sluggish.  Any ideas?

---

### Post by mptpro on 2007-12-08
same problem here.

Using brand new Dell Vostro 1400 with Ubuntu 7.1

Impress was so slow during a group client meeting (30 people!), I had to stop and cancel the meeting!  Very embarassing.  If I can't fix this, I need to return to windows.

Shame.

---

### Post by mptpro on 2007-12-14
update.

I had another meeting scheduled so I decided to try windows openoffice, and, alas it was great!  THhe Impress file I used in my above post was fast, snappy and quick!

The file was created in openoffice on ubuntu, but as mentioned above, when used in ubunutu it extremely slow to the point of not being usable.

I tried it on two computers, both running ununtu 7.1.   One is a dell vostro 1400 desktop and the other is a dell vostro 1500 laptop.

The laptop is a dual-boot ubuntu and windows vista.  On ubuntu it is vey ,very slow, on the same computer, in vista, is a FAST!

Any help is greatly appreciated.

---

### Post by MikeBenza on 2007-12-16
I'm experiencing the same problem.  I found [this thread](http://ubuntuforums.org/showthread.php?t=410244&highlight=open+office+presentation+processor) which suggested I use OpenGL, but that didn't seem to make a difference.  The presentation I'm viewing is a MS Powerpoint presentation.  The processor gets bogged down too if I save the presentation as an ODP presentation too.

The processor use seems to grows as the number of slides increases.  Even when I stop using Impress for a few minutes its CPU usage stays high.

I'm currently on a Sony VAIO with a new-ish installation (about a month).  The graphics card is an ATI Mobility Radeon 9600.  I'm using fglrx.

---

### Post by vanadium on 2007-12-16
No such performance issues here on an X600 Ati Radion. Allegedly, animations on Impress still are not as fluent as on Powerpoint.

---

### Post by wild_oscar on 2008-03-06
I also have the same problem on a high end computer and Ubuntu 7.10. Slideshow is unbearingly sluggish!

It is a powerpoint presentation.

---

### Post by Tomatz on 2008-03-06
Try setting oo to NOT use java and post back results (its in oo tools,options) .

---

### Post by penguins! on 2008-03-17
I'm using a VAIO VGN here too and I get 100% CPU usage in Impress when ppt files are open. 

I'm not even talking about running a slide slow, I just get 100% CPU when the app is open and displaying an open file in slideshow mode or otherwise.

Performance within the app is just about functional but I have a single core CPU and it destroys the rest of my system.

Hmm.. what can we try?

---

### Post by Tomatz on 2008-03-18
Try setting oo to NOT use java and post back results (its in oo tools,options) .

---

### Post by kissamies on 2008-03-26
I'm having exactly the same problem. Disabling the java won't change anything. At first I noticed that my laptop cooler started to yell when using Impress, and then while presentation, it took many seconds to change a slide, even though the slides were kind of simple.

I'm by the way using Opensuse 10.3 at the moment, so this doesn't only seem to be related to ubuntu.

It's pity that this doesn't work, because this makes Windowsless work laptop only a dream. I wonder if Lotus Symphony has any kind of presentation tool...

EDIT: Here seems to be same kind of discussion: [ http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=2871&p=17451#p17451]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=2871&p=17451#p17451")

---

### Post by ThigU on 2008-06-20
I was with the same problem here, a notebook (Ubuntu 8.04) with 2.2 GHz. I changed the "use graphics acceleration" in OpenOffice options tools and the problem was solved. Any idea what was the problem? My graphic card is correctly installed (I can use Compiz effects if I want). 

See ya!

---

