---
title: "Can't remove plams-netbook from Kubuntu Netbook remix 9.10"
date: 2010-03-07
forum: Desktop Environments
---

### Post by applegrew on 2010-03-07
For the past 2hrs I have been struggling to make KDE launch plasma-dekstop instead of plasma-netbook, but all in vain.

I removed, then purged plasma-netbook and plasma-netbook-default-settings packages but after logging out and re-logging in the Netbook UI was back! After restarting the system now I can't even seem to get the KDM. I am greeted with a black screen. :(

Pls suggest.


--- I restarted the system again and the nasty little bugger is back again! This is so frustrating. How do I get plasma-desktop to load instead?

---- Great now I can see that plasma-desktop and plasma-netbook both are running simultaneously! netbook on top of desktop. So my final Q is how do I stop plasma-netbook from loading?

---

### Post by inobe on 2010-03-07
delete or rename .kde folder, this will **reset** your desktop, backup your bookmarks, your data should be fine.

open dolphin and hit view, hit show hidden files, browse for .kde

it will be a plain desktop from when you first started.



restart your machine, done

---

### Post by applegrew on 2010-03-08
Didn't work. :( Deleting that defaulted to netbook ui again as I am running Kubunutu Netbook remix.

---

### Post by inobe on 2010-03-08
are you trying to have a plain desktop with folder view, if yes' i don't blame you, however is **kubuntu desktop** installed ?

not too familiar with the netbook thing as you can already see

---

### Post by applegrew on 2010-03-08
yup kubuntu desktop is installed and this too simultaneously runs with netbook one, but the netbook one displays on top of it.

---

### Post by inobe on 2010-03-08
in kde 4.4 their is a bug, when i enable the netbook display i am unable to switch back to plasma desktop.

do you have kde 4.4 installed ?

if yes' maybe removing plasma-netbook package ?


this fella is trying to install the plasma-netbook :-k

[http://ubuntuforums.org/showthread.php?p=8824452](http://ubuntuforums.org/showthread.php?p=8824452)

---

### Post by applegrew on 2010-03-08
Yup already tried that but somehow it 'reinstalls itself'! It is stuck like straw in a cement. I have now begun downloading non-netbook version. Since now somehow now kwin is crashing always after a system restart. It feels like a row of tumbling bicycles. Now I will have to re-download and re-install everthing from scratch again. I dunno what kind of glue the developers used to paste in the netbook ui.

---

### Post by inobe on 2010-03-08
i'm certain you can install kubuntu 9.10 without issues besides resolution troubles, if that's the case' choose safe graphics when you install.

what kind of netbook you have there ?

you mentioned kwin, did you have desktop affects ?

---

### Post by applegrew on 2010-03-08
This is not a netbook, but I installed the netbook version as I didn't want to wait to dowload the desktop version.

Yup kwin started craching just after I installed ATI FGLRX drivers.

---

### Post by inobe on 2010-03-08
i hear horror stories about ati drivers.

btw even if you wait and get kubuntu 9.10 you may as well request a cd sent out to you.

---

### Post by applegrew on 2010-03-08
Well the download is complete.. Now moving on to re-formatting.

---

### Post by inobe on 2010-03-08
i hope the wait was worth it.

---

### Post by applegrew on 2010-03-08
> **inobe said:**
> i hope the wait was worth it.

Well yes. Now finally I have a functional desktop. BTW the kwin crashinh issue was directly related to ATI FGLRX driver. It seems there is a bug. I have ATI Mobility Readon 4300

---

### Post by stoobers on 2010-09-09
I had this problem:
I installed ubuntu from cd, then kubuntu-desktop.
I installed kubuntu-netbook.  I didn't like it so i tried to remove it.

It wouldn't remove!  sudo apt-get remove kubuntu-netbook didn't do it!

instead, i used:
sudo apt-get purge plasma-netbook
This caused me to lose the menu along the top of kubuntu-netbook desktop.

Logging out and logging back in (no restart) brought me to my old faithful kde desktop.

Sounds like a bug.

---

