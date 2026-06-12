---
title: "Changing your DE"
date: 2013-12-28
forum: Desktop Environments
---

### Post by sideburns on 2013-12-28
We have a netbook, currently running Unity.  Neither of us likes or wants Unity, so we installed Xfce, logged out and tried to log in using Xfce.  Alas, the only options we have are Unity and "Unity 2D," neither of which is what we want.  If it matters, we installed Xfce using the Software Center and have not rebooted, just logged out and back in several times, trying different possibilities.  I'd really rather not have to install Xubuntu over what we have just to get the DE we want, so I'd appreciate, if possible, a somewhat less heavy-handed solution.

---

### Post by Toz on 2013-12-28
What version of Ubuntu?

Do you have a /usr/share/xsessions/xfce.desktop file? This is the one that would add the xfce option to lightdm.

---

### Post by sideburns on 2013-12-28
It's my sister's box, and I think that she has the most recent LTS version.  We searched for xfce in the software center, selected what looked like the right choice and it installed very quickly.  When we didn't find the Xfce option on login, I tried to install it again, but it said it's already installed.  I'll ask her to check and report back.

---

### Post by Toz on 2013-12-28
Also have her run the following command and post back the results:
```
dpkg -l | grep xfce
```
...to see which xfce packages were installed.

---

### Post by Bucky Ball on 2013-12-28
You install xfce4. That is it. NOT Xubuntu-desktop. You don't want that. In a terminal:

```
sudo apt-get install xfce4
```

Log out, choose from Sessions, log in. No idea about needing to add it to lightdm, but Toz may have a point. I've only ever done what I describe here (and have only used xfce4 for years).

---

### Post by deadflowr on 2013-12-28
In the last LTS precise, searching xfce in the software center opens a list of xfce apps such as squeeze and thunar.
But if you type xfce4 then the xfce-desktop meta-package is listed.
I don't know what is also included in the meta-package, though.
Here, found this
[http://packages.ubuntu.com/precise/xfce4](http://packages.ubuntu.com/precise/xfce4)

---

