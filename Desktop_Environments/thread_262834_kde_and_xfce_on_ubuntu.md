---
title: "kde and xfce on ubuntu"
date: 2006-09-22
forum: Desktop Environments
---

### Post by the_0ne on 2006-09-22
I have a plain ubuntu install, with gnome as the desktop.  I'd like to do some messing with kde and xfce.  I checked out the packages in the synaptic package manager and found a kde-core package, which of course had numerous dependencies.  I'm thinking that's the one I want, but then I found a kubuntu package.  I just want to be able to log in to kde to check it out (it's been awhile since I've worked with kde) is the kde-core package the right one?

Pretty much the same question for xfce, which package do I choose in the package manager?

NOTE:  I tried the ubuntuforums search several times, last night around midnight and today about 10 minutes ago.  I keep getting a database error.  So, if this question has been asked (which I'm sure it has) sorry.

Thanks again for the replies...

---

### Post by whizbaby on 2006-09-22
kubuntu/xubuntu-desktop install the respective DE together with a bunch of associated programs (a.g k3b for kde and xfburn for xfce) so if you really want to experience a DE you should install the *-desktop package. (BTW it is safe to uninstall the *-desktop package (read why in package description in e.g. synaptic), you will be asked for this)

---

### Post by the_0ne on 2006-09-22
> **whizbaby said:**
> kubuntu/xubuntu-desktop install the respective DE together with a bunch of associated programs (a.g k3b for kde and xfburn for xfce) so if you really want to experience a DE you should install the *-desktop package. (BTW it is safe to uninstall the *-desktop package (read why in package description in e.g. synaptic), you will be asked for this)

Thanks for the reply whizbaby...

Wow, ok I see the difference.  Just chose kubuntu-desktop and the package count nearly quadrupled.

Question though, will this just install the kde desktop (and of course all the related programs)?  This will not change my boot loader, so that when the machine boots (after the kubuntu packages install) it still shows ubuntu was the original install, correct?   I won't see the kubuntu banner from now on, right?

---

### Post by whizbaby on 2006-09-22
> **the_0ne said:**
> I won't see the kubuntu banner from now on, right?
Not shure what you want to ask but as long as you don't install kubuntu-artwork-usplash (resp. xubuntu-artwork-usplash) your bootup stays identical.

---

### Post by the_0ne on 2006-09-22
> **whizbaby said:**
> Not shure what you want to ask but as long as you don't install kubuntu-artwork-usplash (resp. xubuntu-artwork-usplash) your bootup stays identical.

That's exactly what I was asking.  :)  And it seems when you choose kubuntu-desktop as the main package, one of the dependencies (or marked packages) is the kubuntu-artwork-usplash.  :(

I just didn't want it to look like I installed kubuntu from the beginning.  I wanted it to look like a plain ubuntu system with the kde desktop.

---

### Post by whizbaby on 2006-09-22
You could try to remove the selection from it (in synaptic).

---

### Post by the_0ne on 2006-09-22
> **whizbaby said:**
> You could try to remove the selection from it (in synaptic).

No problem whizbaby, thanks for your help.  As long as I can get back into gnome and my default desktop, it won't matter about the splash screen.

---

### Post by the_0ne on 2006-09-22
> **whizbaby said:**
> You could try to remove the selection from it (in synaptic).

Just wanted to let you know that worked.  I removed the kubuntu-artwork-usplash package from the package manager and the install went through fine.

Thanks.

---

