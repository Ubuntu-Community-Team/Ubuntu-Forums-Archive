---
title: "Kernel update error"
date: 2005-07-06
forum: Desktop Environments
---

### Post by ibanez88 on 2005-07-06
I'm a newbie so please let me know if this should be posted elsewhere.  I've searched extensively and can't find any info that refers to this exact problem.  I get the following error message when I try to update the kernel via the Ubuntu Update Manager.

E: /var/cache/apt/archives/linux-image-2.6.10-5-686_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211.ko', which is also in package ipw2200

I previously upgraded the ipw2200 package in order to get that working properly on my Averatec 1050 notebook.  Most everything else works fine right now, also can add / remove packages via Synaptec no problem.

I don't know how to post the terminal output for the failed update, copy / paste doesn't work in terminals?  Another message given: 

dpkg-deb: subprocess paste killed by signal (Broken pipe)

Does anyone have experience with this?

---

### Post by Xian on 2005-07-06
See this [THREAD](http://www.ubuntuforums.org/showthread.php?t=46579) for a similar issue.

---

### Post by ibanez88 on 2005-07-07
OK the kernel is installed.  But upon reboot I get 

ipw2200 fatal error

and it seems to have broken both eth0 and eth1?  

edit:
I downloaded ipw2200 on another computer and tried to make but got:

make: *** /lib/modules/2.6.10-5-686/build: No such file or directory.  Stop.
make: *** [modules] Error 2

Looks like I might not have build-essentials installed?  Not sure how I check to see if its there.  If it is not there would I be able to download it as a compressed file from another machine?  Again I'm getting nothing through eth0 or eth1 for some reason.

Any further help would be greatly appreciated.

---

### Post by alastair on 2005-07-07
That's probably "linux-headers" required.

---

### Post by ibanez88 on 2005-07-07
I just re-installed hoary from scratch.

linux-headers, build-essential, gcc are installed.  Still same issue with ipw2200 make, error 2 given.  Also I just saw a similar thread elsewhere.

Now at least the ethernet eth1 works, however if I activate wireless eth0 in gnome, the connection hangs regardless of which I choose in Network Connection.  Only when eth0 is disabled entirely can I use the eth1 connection.

update: I've upgraded the ipw2200 firmware and driver according to this how-to (the last method given there)

[http://ubuntuforums.org/archive/index.php/t-21056.html](http://ubuntuforums.org/archive/index.php/t-21056.html)

Activating eth0 wireless in GUI still seems to break eth1 ethernet connection.

---

### Post by ibanez88 on 2005-07-08
Problem is solved now, I needed to edit my /etc/network/interfaces

Thanks Xian and alastair.

---

