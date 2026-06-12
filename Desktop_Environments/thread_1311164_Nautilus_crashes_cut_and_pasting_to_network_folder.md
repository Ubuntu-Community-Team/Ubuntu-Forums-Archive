---
title: "Nautilus crashes cut and pasting to network folder"
date: 2009-11-02
forum: Desktop Environments
---

### Post by lordbinky on 2009-11-02
My network folder is connected as a bookmark in Nautilus using ssh.  When I cut and paste from my desktop to the ssh network folder, Nautilus crashes, all desktop icons disappear.

This occured with Ubuntu 9.04 and currently occurs with 9.1.  I have also tried it with Linux Mint (based on Ubuntu 9.04), but that is not relevant here.

Does anyone else have this issue?  Has anyone found fix for it?

---

### Post by B0rat on 2009-11-11
I have this happening also. I have now disabled desktop effects as I suspect this to be the issue.

I was selecting many video files from a local HD and copying them to my NAS device. It would crash both Nautilus windows and make the desktop icons disappear.

---

### Post by Maggot on 2009-12-09
Yup, same with me.

Cut a file on local computer over SSH nautilus crashes. If you start nautilus it comes back again.

This occurs on Ubuntu 9.04/9.10 and inherited by mint 7 and 8 as well.

If you just copy file on local machine and paste over SSH then it works fine.

---

### Post by harshl on 2009-12-13
I can also confirm this. It occurs for me regularly when I cut a file from the desktop and paste it into a cifs mount.

Running "nautilus &" from the command line brings everything back as expected.

I found a bug that was filed and is very similar if not the same bug. Bug #393102 found [here]("https://bugs.launchpad.net/ubuntu/+bug/393102").

Sign in and show that the bug affects you if it does so we can get a resolution sooner.

---

