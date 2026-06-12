---
title: "VBA framerate and full screen issues"
date: 2010-01-31
forum: Gaming &amp; Leisure
---

### Post by zbirdman777 on 2010-01-31
Hey guys, I'm having issues with VBA 1.8.0. Anytime I attempt to play a game the framerate is horrible. It looks like your character is skipping around the screen and I can't find a way to make it full screen. I've used VBA before and it was under Options>Video> can't remember from there but the option is gone.

I'm having the same lag problem in Vista as well for some reason.

Hardware:
Dell XPS M1530
2.4 dual core
4gb RAM
Nvidia GForce 8600

Any ideas?

---

### Post by portets on 2010-02-01
if it lags in both, maybe you should try vba-m. an updated fork of vba

or is that what you're using?

---

### Post by NightwishFan on 2010-02-01
How do you get VBA-m? I cannot seem to get more than 80% frame rate in VBA-gtk, and sometimes its constantly 180-250% and lags if I throttle to 100%..

---

### Post by portets on 2010-02-01
if you run 32 bit ubuntu go to

[https://sourceforge.net/project/downloading.php?group_id=212795&filename=visualboyadvance-m_1.8.0.877-1_i386.deb&a=29270826](https://sourceforge.net/project/downloading.php?group_id=212795&filename=visualboyadvance-m_1.8.0.877-1_i386.deb&a=29270826)

i think this ppa has it:

**ppa:ripps818/ppa**

just copy and paste that into:
system>administration>software sources>other software>+add...

then search for it in synaptic. but i'm not sure if it's 32 or 64bit or both in their ppa.

---

### Post by portets on 2010-02-01
and to compile the latest version yourself open a terminal somewhere and do

                             svn co [https://vbam.svn.sourceforge.net/svnroot/vbam/trunk](https://vbam.svn.sourceforge.net/svnroot/vbam/trunk) vbam[FONT=Verdana]


"cmake ."      //yes, there is a space and a period after that

"make"         //you can do "make -j3" for a duel core or "make -j5" for a quad core

"sudo make install"

but i'm not sure what the dependencies are other than cmake and make/gcc
[/FONT]

---

### Post by zbirdman777 on 2010-02-01
I'm just using the VBA that was in the repositories. I tried to download VBA-M but the link on the main website takes me to an empty archive. It's strange. I tried to go there under vista and it was the same, I even borrowed my roomate's Mac and same thing.

Here's where I went: [http://vba-m.com/index.php?ind=downloads&op=section_view&idev=24](http://vba-m.com/index.php?ind=downloads&op=section_view&idev=24)

Btw, I'm using 64 bit Ubuntu. VBA is always running at 100%, lowest I've seen was 98%. The best way I can describe is that its running like a broken record that skips constantly (about once a second).

---

### Post by zbirdman777 on 2010-02-01
Sorry about the double posts but I just downloaded VBA-M. I found it on sourceforge.net but that one didn't work at all. It installed but running it results in absolutely nothing. It didn't give me a choice of installer on sourceforge. "visualboyadvance-m1.8.0.877-1_i386.deb" was the name of the file.

---

### Post by portets on 2010-02-02
looks like you'll have to compile vbam if you want to try it.

---

