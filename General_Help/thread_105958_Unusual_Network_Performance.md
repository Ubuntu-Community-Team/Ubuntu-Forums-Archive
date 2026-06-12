---
title: "Unusual Network Performance?"
date: 2005-12-19
forum: General Help
---

### Post by DJStillman on 2005-12-19
Hell all:

New Breezy user, 686-smp kernel, p4 2.6@3125 on Abit AI7, 1GB OCZ VX Gold @ 240fsb, 3com 3c905 nic.

After a few days of configuring, I have a nice setup that does most of what Windows 2003 server did (using as workstation).  Will have other questions later asfter more fiddling, but for today's:

I am experiencing the best internet speed on this PC ever: full wirespeed 3Mbps cable.  I am understandably thrilled, and downloading lots...  BUT, when I browse to my Windows 2003 Server through places to download files, I top out at 8Mbps.  I use an Intel 510 10/100 enterprise switch, cat6 wiring, and have good nics on the server.  This is a new problem unique to Breezy.  Needless to say, downloading a single 900 MB file taking 35 minutes to do so is frustrating.

Am I missing something?  Would a Linksys LNE100TX v.4 be a better nic?  Or, am I misconfigured?

I eagerly look forward to your assistance.  Hopefully I will become proficient enough to help others soon.

David

---

### Post by DJStillman on 2005-12-20
Well, this is a day out, so I am not sure anyone saw it...

I have checked the switch, btw, and it shows the line at 100BaseT Full Duplex...

Are there other ways to connect to my sever that are known better performers that I can try?

D

---

### Post by BathroomNinja on 2005-12-20
A few questions.

Did you have windows or some other OS on this computer previous to installing Ubuntu?  If so, did this process work at that time?  Also, if so, did you change the way the network was configured since then?

Have you tried using Samba?  I admin a small network that is mixed Ubuntu/Windows.  I have found that using Samba, I can easily move 3 gig files at crazy speeds between the windows and ubuntu computers.  The only bottle necks I ever get are on the windows side when I try to xfr from win to win.  One thing to note however, is that when I move files, I move them from the windows desktop, and drag-n-drop them into the samba share on the ubuntu server.  I don't do it from the ubuntu server, so I don't know if that makes any difference or not.

---

### Post by DJStillman on 2005-12-20
[QUOTE=BathroomNinja]A few questions.

Did you have windows or some other OS on this computer previous to installing Ubuntu?  If so, did this process work at that time?  Also, if so, did you change the way the network was configured since then?

Have you tried using Samba?  I admin a small network that is mixed Ubuntu/Windows.  I have found that using Samba, I can easily move 3 gig files at crazy speeds between the windows and ubuntu computers.  The only bottle necks I ever get are on the windows side when I try to xfr from win to win.  One thing to note however, is that when I move files, I move them from the windows desktop, and drag-n-drop them into the samba share on the ubuntu server.  I don't do it from the ubuntu server, so I don't know if that makes any difference or not.[/QUOTE]

This computer had Windows 2003 Server on it before, and worked well.  I got 50-80Mbps out of it pretty easily.  As for the Samba, isn't that only for transfers FROM Ubuntu?  I am using Ubuntu on my workstation, and downloading from my Windows 2003 Server.  It is like there is some cap on this new Breezy that is slowing me down...

---

### Post by yanik on 2005-12-20
Interesting.  Can you post back if you find a solution?  I have a similar problem.

---

### Post by BathroomNinja on 2005-12-20
I'm really not sure.  Try this for me, just for my sheer curiosity.  Go with me here.

Install Samba on Ubuntu.(plenty of HOWTO's on it, just do a quick search)

Setup a Samaba shared folder with NO passwords or anything crazy like that.  Readable and writtable by all.

Use Network Neighborhood to find that share, and map it to a network drive in Windows Server.

Using your Windows Server computer, drag and drop a huge file (as big as you can find) into that share.  Time it.

Now, go back to the Ubuntu computer, and use the process you are currently using to move the same file over.  Time it.

Which is faster?  I'm really curious here as to what happens.  I really think this will help narrow down the problem.  Then again, I'm a ninja.  Of Bathrooms.

---

