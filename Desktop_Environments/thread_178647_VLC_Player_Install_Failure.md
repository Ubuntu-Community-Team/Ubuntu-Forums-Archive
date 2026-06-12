---
title: "VLC Player Install Failure"
date: 2006-05-18
forum: Desktop Environments
---

### Post by Incorp on 2006-05-18
Keep recieving errors saying that files are not installable???

I cant live without my VLC, can anyone help?

---

### Post by louis_nichols on 2006-05-18
Well... In order to properly troubleshoot such problems, one needs some more details, like: what version of Ubuntu are you using? Can you paste here the exact errors you get while trying to install? And also, to correctly troubleshoot this, we need the contents of your sources.list under /etc/apt

My first guess would be that you don't have all repos enabled. So, first thing you might want to try is:

1. Backup your sources.list like this:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

2. Open it for editing:

gksudo gedit /etc/apt/sources.list

3. Delete the character **#** in front of every line that starts with **deb** or **deb-src**

4. Try installing again:

sudo apt-get update && sudo apt-get install vlc

---

### Post by Incorp on 2006-05-18
using V5.10, I was installing wxvlc, and it comes up with the following:

wxvlc:
 Depends: vlc but it is not going to be installed
 Depends: libwxgtk2.4-1 but it is not going to be installed

I will try your sugesstion now and report back

Thanks.

EDIT:

Terminal shows following:

(gedit:17788): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

then the file that opens for editing is empty, maybe this is my problem?

---

### Post by louis_nichols on 2006-05-18
oh. well, then use *sudo* instead of *gksudo.* sorry about that, it shouldn't happen that way, but why it happens should be a whole new thread I think.

---

### Post by Incorp on 2006-05-18
Sorry, its working now that i am doing it through terminal, many thanks for your help, soon as i did it through terminal it said i have 112Mb of updates as well.

---

### Post by louis_nichols on 2006-05-18
glad it's working. as for the updates... well, that happens. What I usually do if the packages to be donwnloaded would take a lot of time, I set it to update during the night and shutdown when it's done. works great.

---

