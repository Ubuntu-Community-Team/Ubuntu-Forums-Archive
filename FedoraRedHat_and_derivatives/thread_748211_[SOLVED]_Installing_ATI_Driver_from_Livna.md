---
title: "[SOLVED] Installing ATI Driver from Livna"
date: 2008-04-07
forum: Fedora/RedHat and derivatives
---

### Post by cprofitt on 2008-04-07
I am trying to use the Livna instructions for installing the ATI driver, but keep getting this error:

Error: ati-x11-drv conflicts with xorg-x11-drv-fglrx

I am about to Google, but if someone else has an answer feel free to reply.

Also, are the Livna repos -- good to use?

I will update if I find a Google answer.

---

### Post by cprofitt on 2008-04-07
I found the answer for those that are also looking...

yum --disablerepo=freshrpms install kmod-fglrx

The conflict was the driver (for F7) that was in the freshrpms repo.

---

### Post by Antman on 2008-04-07
I haven't used the freshrpms repo yet. I tend to stick with Livna and Fedora repos. So far I haven't had any issues yet.

---

### Post by igknighted on 2008-04-07
yeah... don't mix FreshRPMs and Livna on your system, the packages can conflict.  There is a project underway to merge them (as well as a few others), its called "RPM-Fusion", check it out on google, but it isn't ready yet.  Hopefully for F9.

The biggest difference between Livna's drivers and FreshRPMs is that Livna uses kmod's like ubuntu, but that also means that you can't upgrade until the livna packager builds the kmod for the new kernel.  FreshRPMs uses dkms (dynamic kernel module system, IIRC) which checks at bootup to ensure that a kernel module is available, and builds one if it isn't found.  I use Livna because I find dkms confusing at times, but I can recognize that it is in many ways superior to using a pre-built kernel module.

---

### Post by pelle.k on 2008-04-19
> FreshRPMs uses dkms (dynamic kernel module system, IIRC) which checks at bootup to ensure that a kernel module is available, and builds one if it isn't found.The day i found that out, i seriously started using fedora. I always had problems with livna being out of sync with fedora, and that gave me a "bad vibe" in fedora, even though livna isn't really a official fedora repo it was the only way of getting my nvidia running.
I love DKMS.

---

