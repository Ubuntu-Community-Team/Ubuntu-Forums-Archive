---
title: "Significant progress in feisty 20070131 desktop amd64 (vmware)"
date: 2007-01-31
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-31
After almost a week of troubles, today's feisty amd64 desktop build shows significant progress (I am always testing in vmware), so I felt like posting a small report regarding the bugfixes :-)

Network connectivity of the live cd that was broken for 2 days, is now restored.

Partitioning and formatting the (blank) hard disk (well-known huge bug) during installation works flawlessly.

After the first boot, there appears a crash report, which however does not create a crash file and cannot be submitted. This crash does not reappear in subsequent boots. It must be some kind of 'ghost' report, given that just booting the live cd (without any installation), there exists a "preinstalled" bug about update-app-install in /var/crash (which is a well known bug, not yet fixed).

Also, running update manager from gnome panel works flawlessly (no crash), but judging from the related bug reports in Launchpad in various environments, I feel that this bug may reappear in the following daily builds.

During the boot of the installed feisty, you will see 3-4 pages of debugging messages related to access to ata1 and ata2, before reaching the fchk stage where the kernel checks the filesystem and finally boots. These must be artifacts due to incompatibilites with the way vmware accesses the hard disk and the cd and I expect will be soon ironed out. Installing on a real system might not cause such messages.

Finally, shutting down the live cd session does not show the familiar splash "remove the cd and press enter", but it's not a big deal.

I feel very happy regarding the above definitive signs of progress and I recommend everybody to get and test this (or subsequent) builds. Booting the from the iso and the installation process are lightning fast and really impressive. If you have enough memory, make sure to assign 512 MB memory for the feisty vm, because otherwise the installer makes unnecessary accesses to the iso that slow down the installation process significantly.

Update: Installing vmware tools works flawlessly too, the tools iso is mounted normally (did not work in previous builds)

---

### Post by spd106 on 2007-01-31
I also saw a crash report with the i386 version. It said that add/remove programs had crashed, which is odd because I never started it. Everything else seems ok except that it won't shutdown properly. I get the Usplash image, it just doesn't turn off.

So when do we start testing? I'm currently monitoring [https://bugs.launchpad.net/ubuntu-iso-tests/+bugs](https://bugs.launchpad.net/ubuntu-iso-tests/+bugs) for the images to appear, nothing so far. I don't want to burn any cds until I know that I have a release candidate. So it's vmware/virtual pc at the moment.

---

### Post by UBfusion on 2007-01-31
According today's [sticky post by Henrik]("http://www.ubuntuforums.org/showthread.php?t=350126"), expect a frozen version in 1-2 days!

---

### Post by pochu on 2007-02-02
> **spd106 said:**
> I also saw a crash report with the i386 version. It said that add/remove programs had crashed, which is odd because I never started it. Everything else seems ok except that it won't shutdown properly. I get the Usplash image, it just doesn't turn off.

So when do we start testing? I'm currently monitoring [https://bugs.launchpad.net/ubuntu-iso-tests/+bugs](https://bugs.launchpad.net/ubuntu-iso-tests/+bugs) for the images to appear, nothing so far. I don't want to burn any cds until I know that I have a release candidate. So it's vmware/virtual pc at the moment.
You can test now. And the add/remove bug should be fixed (at least the fix has been commited).

Regards
Pochu

---

### Post by spd106 on 2007-02-02
Sadly no, the bug remains and now herd 3 is released it is too late. I've marked my bug report [#82722]("https://launchpad.net/ubuntu/+source/gnome-app-install/+bug/82722") as a duplicate of bug [#80589]("https://launchpad.net/ubuntu/+source/gnome-app-install/+bug/80589") with the fix. I guess I was just too quick to post a new bug report, I'll try to be more thorough in future.

---

### Post by pochu on 2007-02-03
As I commented on the bug report, could you try to run 
```
sudo aptitude update && sudo aptitude install gnome-app-install
```
before running the installer?

Regards
Pochu

---

