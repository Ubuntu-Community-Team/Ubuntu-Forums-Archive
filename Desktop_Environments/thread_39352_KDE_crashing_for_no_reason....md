---
title: "KDE crashing for no reason..."
date: 2005-06-04
forum: Desktop Environments
---

### Post by Krash1201 on 2005-06-04
finally got all of Kubuntu isntalled on my laptop, including wireless.  at the building i am at there are about 10 wifi networks.  so i use the kwifimanager access them, but after connecting KDE hangs and won't do anything.  it either restarts its self or i have to manually shut it down with the power switch.  any ideas?

---

### Post by Matt05 on 2005-06-05
In general, you will get more useful answers when you provide more information.  Not all laptops are created equal.  So which one are you using?  Same for wireless card.  Also, did you make sure that your machine runs stable without wireless?

E.g., I had trouble getting kubuntu run reasonably stable on a Dell D610.  The error showed up mostly when I accessed the network (wireless or ethernet).  The fix was to install the latest kernel from breezy.

---

### Post by GeneralZod on 2005-06-05
My entire laptop (Mitac 7321 with PCMCIA orinoco-based wireless card) will reliably hard-lock after 30 mins or so of using KWifiManager - without KWifiManager, it runs and runs. We should probably file a bug report, as there seems to be something odd going on here.  Anyone else having trouble with KWifiManager?

---

### Post by janrinok on 2005-06-05
Krash
Does the laptop crash after a certain period of operating (30secs, 10mins, 1 hour?) or is it dependent on the amount of internet access?  What were you doing at the time of the crash, or does it still crash if you boot it up but do nothing else?  Even if you don't log on?  We will need more information if we are to pin-point what might be causing the crash, and then we can try to fix it.  Jan

---

### Post by Krash1201 on 2005-06-06
i run a dell inspiron 8600 with the broadcom based dell 1350 minipci wifi adapter.  i have the wifi card installed with the ndis wrapper work around.  my system runs perfect when jacked into my lan via cat5, but the problem only happens when i am running wireless, and in firefox.  kaffine and ff both crash seemingly at random, and this whole time i have been using kwifimanager as a gui to operate my connection.  for the most part everything else is running fine.  i have loaded wlassistant and i am giong to try that instead of kwifimanager.  i am getting errors with the executables and permissions with wlassistant though.  any ideas?

---

### Post by daller on 2005-09-03
Does Kwifimanager work at all?

I've installed kubuntu on more than 10 different laptops for now, and none of them seems to work with kwifimanager.

Most likely, statistics like these points at failure 40 (40 centimetres away from the monitor)

But I simply can't get it to work - not even with unencrypted networks...

---

### Post by godzero on 2005-09-03
Is it a "hard freeze"? EG: can you ctrl-alt-backspace or ctrl-alt-f1?

Which kernel version are you running?

"hard freezes" are usually kernel related. Inotify is a serious issue with the 2.6.11 version and manifests itself as hard freezes while browsing (especially the file system).

EDIT: Clarity.

---

### Post by daller on 2005-09-03
[QUOTE=Krash1201]i run a dell inspiron 8600 with the broadcom based dell 1350 minipci wifi adapter.  i have the wifi card installed with the ndis wrapper work around.  my system runs perfect when jacked into my lan via cat5, but the problem only happens when i am running wireless, and in firefox.  kaffine and ff both crash seemingly at random, and this whole time i have been using kwifimanager as a gui to operate my connection.  for the most part everything else is running fine.  i have loaded wlassistant and i am giong to try that instead of kwifimanager.  i am getting errors with the executables and permissions with wlassistant though.  any ideas?[/QUOTE]

How did you install wlassistant? From source or deb?

Installing from source, I'm stuck during "make"! (wlassistant.moc:204: fatal error: opening dependency file .deps/wlassistant.Tpo: Permission denied)

Installing from deb-repos, I get dependency-problems!

wlassistant: 
Depends: kdelibs4c2 (>= 4:3.4.2-1) but 4:3.4.2-0ubuntu4 will be installed
Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 will be installed
Depends: libxrender1 (> 1:0.9.0-1) but 1:0.9.0-1 will be installed

Any suggestions?

---

