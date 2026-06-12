---
title: "[SOLVED] Nautilus search with gksudo freezing"
date: 2008-05-30
forum: Desktop Environments
---

### Post by NilsE on 2008-05-30
Since doing the updates in the attached screen shot whenever I open Nautilus as root ( gksudo nautilus) and do a file search it freezes at 100% cpu.  If I force kill it, it ends but Nautilus stays at 100% until a reboot. If I do a file search within Nautilus as a regular user it works fine.

I have tried re-installing the older versions of the obvious packages with Nautilus in them with no help.

Has anyone else experienced this or have an idea on what to try.

---

### Post by NilsE on 2008-06-05
I am still having this problem no matter what I try and I am guessing no one else is having the problem since there were no replies.

After many many tries at reinstalling various things I did a fresh install of 8.04 and did all the updates and it was working.  I then opened the proposed repository to get FF3 RC1 and it's dependencies which appears to be all of the FF3 packages, xulrunner and yelp. That's when it appears to have stopped working again.  

If I try to remove or back level xulrunner it wants to remove everything FF related.

I am lost here and have no idea where to go with this or debug it since when it freezes there are no log entires even after the force kill.

---

### Post by NilsE on 2008-06-09
I found one other person that is having the same problem accept he has not opened the proposed repositories so it appears to happen with the normal updates.

Could someone who is up to date with updates try the following and see what happens

1) In a terminal

gksudo nautilus

2) In nautilus click on the search button and try to find a file you know is there.

And let me know what happens.

If it does freeze on you you can force kill it by clicking on the X then go into a terminal and do a top to get the PID for nautilus (should be 100% cpu).  Then do a sudo kill -9 xxxx  where xxxx is the pid from the top command. OR simply reboot.

---

### Post by Xiong Chiamiov on 2008-06-09
Confirmed.  I'm using the standard repos (plus a few) and keep up-to-date, and I get this behavior.  I'm using KDE atm, but that shouldn't affect anything.  Same thing happened when I ran nautilus using kdesudo, though I was able to kill it just by ctrl-c in the terminal window (the first time, with gksudo, I had to use "sudo killall nautilus").

I don't use nautilus (much less as root), so I can't say how long this has happening.  It's possible that many people are affected, but just don't know.  Consider filing a bug report on Launchpad?

---

### Post by NilsE on 2008-06-09
Thanks for confirming the problem.  I will file a bug but was waiting to see if it was just me.

---

### Post by VMC on 2008-06-09
Same here. Also using the Terminal I get the following errors:
vmc@vmc-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6118): WARNING **: Unable to add monitor: Operation not supported

---

### Post by NilsE on 2008-06-10
VMC

Possible fix to one of your problems is to remove nautilus-share but only if you are not sharing. However, the message really is only telling you that you are not sharing or atleast nautilus thinks your not. 

The monitor message is and old problem but does not seem to cause any real issues.

---

### Post by dupersuper on 2008-06-10
i have another problem which is gksudo nautilus freeze when accessing the trash. 
it happened only after a recent update.
seems that there is problem with nautilus running under root.

---

### Post by NilsE on 2008-06-10
I have been browsing all of the bugs that are related to nautilus and found a number that are against gvfs, tracker and just against nautilus and have found many that are similar to this problem such as the one about root access freezing on the goto trash folder option. It appears to be a memory leak.

In one or two of them a workaround was suggested for when nautilus is run as root.

Try launching root nautilus with the following command:
```

gksudo dbus-launch nautilus
```

---

### Post by NilsE on 2008-07-25
Todays update for gvfs in Hardy proposed repository solved this problem. It should also have solved the freezing when going to the trash folder or emptying trash.

---

