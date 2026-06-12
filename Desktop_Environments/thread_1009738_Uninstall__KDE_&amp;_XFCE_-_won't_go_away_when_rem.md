---
title: "Uninstall:  KDE &amp; XFCE - won't go away when removed in terminal or Synaptic"
date: 2008-12-12
forum: Desktop Environments
---

### Post by uncle giggles on 2008-12-12
Hey folks, first post, first problem.

Using Ubuntu x64 8.10.  I started with and learned to love GNOME, but yesterday I decided to try out KDE and XFCE just for fun.  Used Synaptic to get kubuntu-desktop and xubuntu-desktop (plus all additional packages for both) just to see if I liked them.  I never set either of them as the default environment, just for this session.  Turns out I didn't like either of them and tried to uninstall them with the following commands as another thread on here instructed -
```
sudo apt-get remove kubuntu-desktop
sudo apt-get remove xubuntu-desktop
```  Here's the output for both commands:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Why did these commands fail?  How could it not know they were installed?  That was a bit confusing, so I rebooted the system just for good measure, and this is where it gets weird - The startup screen after POST shows the Kubuntu screen, then the login screen shows the Xubuntu screen, and when I logged in without changing the environments it defaulted to GNOME.  Weird.  

Went into Synaptic and it showed both as still installed.  I marked both kubuntu-desktop and xubuntu-desktop as "Mark for Complete Removal".  It succeeded and showed them as uninstalled, and I rebooted the system again.  Wouldn't you know it, but both are still there in the Sessions menu and the boot/login screens are still screwed up, plus I can still log into both fully functional even though Synaptic shows that they are both uninstalled.

I'm lost.  Do I actually have to shuffle through Synaptic and remove every single package that was installed with Ku and Xu?  I'd rather not waste time with that unless I knew exactly what to look for.  But even then, if K-desktop and X-desktop were "removed" then why the heck are they still here anyway?

Ideas?  Thanks!

---

### Post by cdtech on 2008-12-12
Try this site:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by cdtech on 2008-12-13
I also installed KDE after I installed Gnome but I used the following technique to prevent KDE apps from showing up in the Gnome menu and vice-versa, just something you could concider:

If you use the Gnome desktop (like I do) try this:
Make a backup:
```
mkdir ~/.desktopbackup
cp -R /usr/share/applications/ ~/.desktopbackup
```
On a command line type:
```
for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done
```

You could also do the same with KDE by changing it to:
```
for i in /usr/share/applications/*; do echo "OnlyShowIn=GNOME;" | sudo tee -a $i; done
```

Hope this helps.........

---

### Post by uncle giggles on 2008-12-13
> **cdtech said:**
> Try this site:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)Well that worked flawlessly.

Problem completely solved.  Thanks!

---

