---
title: "dependency-hell with glibc - can't update"
date: 2017-11-29
forum: Desktop Environments
---

### Post by mco404 on 2017-11-29
Hi guys, it's great to be in the forum with you.

I'm trying to install megasync whic is a backup & sync client for a cloud service. However, the installation seems to need more up-to-date glibc versions, **however I am not able to update to those versions.**

The output when I install the megasync deb package with aptitude is as follows:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'megasync' instead of './megasync-xUbuntu_17.10_amd64(1).deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
[B] megasync : Depends: libc6 (>= 2.25) but 2.24-9ubuntu2.2 is to be installed
            Depends: libqt5core5a (>= 5.9.0~beta) but 5.7.1+dfsg-2ubuntu4~1.17.04.1 is to be installed
            Depends: libqt5gui5 (>= 5.8.0) but 5.7.1+dfsg-2ubuntu4~1.17.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.[/B]

```

However, when I update, for example, libc6 I get the following message:
```
libc6 is already the newest version (2.24-9ubuntu2.2).
```

How could I possibly update the problematic dependencies?

Thanks for your help in advance!

[B]What I already tried:

[/B]* All the automatic updates/fixes (apt update,upgrade,dist-upgrade,-f,clean,etc..)
* Removed all PPA

---

### Post by ajgreeny on 2017-11-30
You have this thread marked as **SOLVED**.

Is that correct?  
If so, please tell us what the solution was as it may help others who have the same problem.

---

### Post by mco404 on 2017-11-30
Hi, yes I solved it. To be honest I did not write the answer because the solution was stupid as hell. For some reason I thought that my version was 17.10 and so I downloaded the 17.10 deb file. However, my version is actually 17.04.... so yeah. A stupid mistake by me.

---

