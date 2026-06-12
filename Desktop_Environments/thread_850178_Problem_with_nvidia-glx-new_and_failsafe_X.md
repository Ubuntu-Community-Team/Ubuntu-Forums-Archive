---
title: "Problem with nvidia-glx-new and failsafe X"
date: 2008-07-05
forum: Desktop Environments
---

### Post by PeEllAvaj on 2008-07-05
**Goal:**I want to get nvidia-glx-new working on my computer.

**Background:**
About a year ago I had a working configuring using nvidia-glx-new (the ubuntu package of the nvidia proprietary driver).  I then had some problems playing an opengl game, so I switched over to the proprietary driver, directly from their website (not managed by package system).  

The proprietary driver didn't fix anything, and I eventually solved the problem outside of the driver.  I didn't switch back, because everything was working fine.

The problem was that whenever an update would come out for any of the restricted packages, the package manager would break my proprietary nvidia driver installation.

I have attempted to re-install and dkpg-reconfigure all of my xserver and nvidia related pacakges in an attempt to switch back to the ubuntu version of nvidia-glx-new, but no matter what I do, bootup of X breaks and drops into failsafe mode, and after about 6 seconds, failsafe mode breaks and I end up with a black screen, and no ability to switch terminals (although the server is 100% up over sshd).

I would appreciate ANY help anyone can provide!  Let me know if there is any files or details I can provide.

---

### Post by zzatz on 2008-07-05
I had horrible results trying to use the Ubuntu-packaged Nvidia proprietary drivers. What worked for me was to purge all Ubuntu packages involving Nvidia and manually run the installer downloaded from Nvidia.

I understand and accept that I need to keep track of updates manually, and that I need to rerun the installer whenever the kernel changes. But it works, and nvidia-glx-new didn't.

dpkg -l | grep nvidia

apt-get purge whatever_dpkg_listed

I believe that I purged nvidia-glx-new and some flavor of linux-restricted-modules.

---

### Post by PeEllAvaj on 2008-07-05
That isn't the answer I wanted, But it is an answer I can live with, :).

Thank you so much!
PeEll

---

