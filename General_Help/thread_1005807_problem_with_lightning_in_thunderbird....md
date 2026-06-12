---
title: "problem with lightning in thunderbird..."
date: 2008-12-08
forum: General Help
---

### Post by Mia_tech on 2008-12-08
I've decided to wipe clean my pc, and install 8.10, but before I made a backup of my .mozilla and .mozilla-thunderbird folders, so I could restore them after the clean install then only problem is that lightning addon in thunderbird stopped working, I'm not able to create any events in calendar or tasks... I did uninstall and reinstall the addon with no changes, to make sure I took ownership of the .thunderbird folder thinking a permission issue.. but still same results, could someone give me a heads up with this problem.


thanks

---

### Post by boredcollegekid on 2008-12-08
Make sure you have the libstdc++5 package installed. Lightning requires it and it wasn't installed on my system, installing it fixed my issues with Lightning.

---

### Post by Mia_tech on 2008-12-09
I installed  it, but that wasn't it... still looking

---

### Post by Mia_tech on 2008-12-09
actually that was indeed the problem a bug reported in lighning 0.9 in ubuntu 8.10, the only thing is that after installing the lib file, the lighning addon needed to be reinstalled.... but now everything is working fine


thanks

---

### Post by germanix on 2008-12-11
Hi Boredcollegekid, I have exactly the same problem as Mia-tech. I used your advice and everything works now. I thank you for this post.

---

### Post by dobuntu on 2009-01-21
I had the exact same problem, I was going mad, your direction worked for me too! Thanks a lot!

---

### Post by bastubis on 2009-02-04
Doesn't work for me, still can't get bi-directional connection to Google using Ubuntu 8.04, Thunderbird 2.0.0.19, Lightning 0.9, Provider 0.5.1. 

There's a bug report [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853) 

So I removed Provider and Lightning, installed libstdc++5, reinstalled Lightning and Provider - Lightning now works better than it did but 'new calendar' still greyed out. Took off Provider and can now create a new calendar but it's not much use cos I can't connect to Google without Provider.

---

### Post by khachik_nazaryan on 2009-02-04
Hello All

I had the similar problem with my thunderbird lightning.
Thanks a lot, the proposed solution worked for. I just reinstalled libstdc++5, then reinstalled lightning and everything started to work properly.

Thanks again!

---

### Post by pete on 2009-03-14
Excellent! boredcollegekid's solution fixed the issue for me as well.

---

### Post by cgul1 on 2010-07-26
This is an old thread but perhaps you stumbled upon it.
I have TB 3.5 with new lightning as of 7/2010
found I could not add a new task.
I was using Google calendar(s) and no local calendar
apparently you have to have a calendar ie default on the local machine for tasks. I added one back in and tasks works again.

---

