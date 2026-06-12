---
title: "Text obscured in Firefox URL bar"
date: 2014-05-04
forum: Desktop Environments
---

### Post by benpont on 2014-05-04
I just did a fresh install of Lubuntu 14.04 and everything works fine except for this problem (see screen cap):

[IMG]http://i.imgur.com/wS7SG4u.png[/IMG]

I've deleted my profile, tried different themes, disabled extensions, started in safe mode, reinstalled firefox, went to google and IRC for help, etc.  Nothing is working.  Hoping someone can help here.  I can't be the only one who has encountered this issue.

---

### Post by Otto-C on 2014-05-04
Your not.  Same issue with Xubuntu.

---

### Post by benpont on 2014-05-04
Um...so any advice/suggestions?  Is there another thread where this issue is discussed?

---

### Post by benpont on 2014-05-04
> **Otto-C said:**
> Your not.  Same issue with Xubuntu.

What if I downgraded to Lubuntu 12.04?  Would it matter?

---

### Post by mörgæs on 2014-05-04
It would be a bad idea, as Lubuntu 12.04 is no longer supported.
I suggest using another browser for some days waiting for a fix to arrive.

---

### Post by benpont on 2014-05-04
> **mörgæs said:**
> It would be a bad idea, as Lubuntu 12.04 is no longer supported.
I suggest using another browser for some days waiting for a fix to arrive.

So this is a known issue and a bug report has been filed?

---

### Post by kalehrl on 2014-05-04
Same here:
[https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007391.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007391.html)

---

### Post by mörgæs on 2014-05-05
> **benpont said:**
> So this is a known issue and a bug report has been filed?

I don't know, you tell me:
[https://bugs.launchpad.net/ubuntu/+source/firefox](https://bugs.launchpad.net/ubuntu/+source/firefox)

What I meant was that it is a very obvious error. It's likely that a developer is aware of it, at least if it was me I would wait for the next release before taking action.

---

### Post by benpont on 2014-05-05
> **mörgæs said:**
> I don't know, you tell me:
[https://bugs.launchpad.net/ubuntu/+source/firefox](https://bugs.launchpad.net/ubuntu/+source/firefox)


It's not a firefox bug. The address bar renders perfectly in other distros.  The bug is likely with lxde.

---

### Post by vasa1 on 2014-05-05
> **benpont said:**
> It's not a firefox bug. The address bar renders perfectly in other distros.  The bug is likely with lxde.
I don't know about that. I use Firefox on Lubuntu 14.04 and don't have the problem.

---

### Post by kalehrl on 2014-05-05
I'm willing to file a bug report but I'm not sure against what package?

---

### Post by kalehrl on 2014-05-05
The bug has already been reported here:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1316250](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1316250)

---

### Post by Handssolow on 2014-05-06
Here too, Ubuntu 12.04 LTS  on a single core Toshiba Satallite laptop after I updated to Firefox 29.0 today.
Sometimes if I refresh the screen the grey/black or black bar goes and I see the web address.

---

### Post by kalehrl on 2014-05-06
That graphics do you have in your laptop?

---

### Post by Handssolow on 2014-05-06
My laptop is a Toshiba Satellite M35X-S114 with intel i855 chipset where I have this problem.
On two desktops with Ubuntu 12.04, Firefox 29.0 seems to run normally.

---

### Post by vasa1 on 2014-05-08
> **benpont said:**
> It's not a firefox bug. The address bar renders perfectly in other distros.  The bug is likely with lxde.
Now reports of the same issue (I think) are appearing in the **Xubuntu** users mailing list:
[https://lists.ubuntu.com/archives/xubuntu-users/2014-May/006916.html](https://lists.ubuntu.com/archives/xubuntu-users/2014-May/006916.html)

---

### Post by vasa1 on 2014-05-08
While the Xubuntu mailing list suggests one workaround, the topic is in Mozilla's bugzilla as well and this setting seems to fix the issue for some: [https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c23](https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c23)

---

### Post by Handssolow on 2014-05-09
Yes, this bug fix worked on my Toshiba Laptop with its Intel i855 chipset graphics.

---

### Post by crisrcraft on 2014-06-07
FYI, I'm also getting the same exact problem with Firefox, I rely mostly on Chrome now. Looks like my problems began about the same time as you (in May), I'm on Xubuntu.

---

### Post by crisrcraft on 2014-06-07
This will fix it, go to Firefox, enter the below in the url, search for gfx.xrender.enabled and set it to FALSE. Restart Firefox, problem solved.

about:config
gfx.xrender.enabled;[B]false

[/B][https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c24](https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c24)

---

