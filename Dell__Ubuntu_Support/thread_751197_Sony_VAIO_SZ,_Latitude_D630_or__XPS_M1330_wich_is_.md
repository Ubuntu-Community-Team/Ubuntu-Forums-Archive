---
title: "Sony VAIO SZ, Latitude D630 or  XPS M1330 wich is better for  ubuntu ???"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by m.h.shams on 2008-04-10
Hi Friends,

After a long time using Ubunt (from 5.10) on my PC WorkStation
for Programming. I am going to bye a NotBook.

Candidates are :

1 - DELL Latitude D630

2 - DELL XPS M1330

3 - SONY VAIO SZ SERIES

MODEM and again MODEM is very important for my work.

for ubuntu 7.10 (or 8.04),


which is your choice ????
which have better compatibility with ubuntu ?????
anyone have experience with these notebooks MODEM in UBUNTU ?


thanks all

---

### Post by notwen on 2008-04-10
Try to not post duplicate threads, especially in the span of 15min.  Please refer to your **[original thread]("http://ubuntuforums.org/showthread.php?t=751183")** for my response.

---EDIT---
Mods removed your other thread.

I know Dell offers the [XPS M1330 pre-installed w/ Ubuntu]("http://configure.us.dell.com/dellstore/config.aspx?oc=dycwtu1&c=us&l=en&s=dhs&cs=19&kc=segtopic~linux_3x") and the N Series model(pre-installed models) offers a $20 external modem when configuring it.  I don't believe Dell would offer the option if there were any issues w/ using the modem, so it appears to be a fully functional laptop pre-installed w/ Ubuntu, you just need to add the modem.  

Are you in the US or a country where Dell is offering the pre-installed Ubuntu systems?  I own a Inspiron 1420n and have been nothing but satisfied w/ my Dell system pre-installed w/ Ubuntu.  If not, you could make a exact replica of the XPS M1330, except purchase the Windows Vista machine and come back and re-install Dell's custom Ubuntu image available [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") at Dell's Linux Wiki.

I cannot comment on the other two models as far as hardware recognition/compatibility goes, but you may want to research their hardware and search for any issues relating to them.  Best of luck w/ your future purchase.  =]

---

### Post by rzz on 2008-04-10
Actually, I have both D620 (Duo Core 1) and M1330.
I bought this M1330 a couple of month ago and passes the old D620 to my mom.

Ubuntu doesn't pick up the D620 wireless card really well. I have to use ndiswrapper as driver and run some nhcp commends on start up. This also forces my mom to stick with the XP. M1330, on the other hand, runs like a charm with 8.04 beta LiveCD, wireless, remote control, webcam, bluetooth, media buttons, except a bug with internal microphone, which can be solved by installing linux-backports.  

Anyway, D630 is more a *business* type laptop. By business, I mean heavy and thick. I may know that if you hands-on with it for some time.

As 8.04 can pick up wifi when running naked on M1330, I have doubt on modem.

---

### Post by m.h.shams on 2008-04-12
first of all im sorry about duplicated thread, i made  a mistake and i thought that my thread was not post.


any idea about D630 or sony ???

---

### Post by Scotty Bones on 2008-04-21
If you decide to go with the SONY, I would highly suggest creating the recovery set before attempting to do anything else.  SONY's do not come with a physical restore set, they are included on a hidden recovery partition that can be accessed with the F-10 key at boot.  If you don't create them ( done from inside windows, control panel, VIAO Recovery Wizard) and end up needing them later you have to purchase them.  They are usually about $30 a pop and thats only if they are available in stock, if not, its off to the depot for re-imaging. 

The only thing on the NB I can think of that won't work is the special function keys and the vol control next to the KB.  These are handled by the SONY NB Controls driver and I don't know if there is an open equivalent, you might be able to check around the forum for a solution.

I stopped working for SONY tech support just before I started to use Ubuntu, so I never had the opportunity to check out a live-cd on one of them.  You could try stopping by a local retail store (Best-Buy should carry them) and load one up yourself to see if all is fine (they may get a little pissie though).

Also, if you like the SZ you may also want to check out the FS.  They should be fairly comparable in both HW and price.  The added advantage is that the FS comes with on-site service included in the warranty.

---

