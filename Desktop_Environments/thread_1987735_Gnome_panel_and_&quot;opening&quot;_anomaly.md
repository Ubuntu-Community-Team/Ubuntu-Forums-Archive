---
title: "Gnome panel and &quot;opening&quot; anomaly"
date: 2012-05-26
forum: Desktop Environments
---

### Post by forcecore on 2012-05-26
when opening something then there stays strange delayed opening and after some 14 seconds it dissapears. It is just annoyng nothing more. If there is some related bug please post link here, thanks.

Ubuntu 12.04 x64

---

### Post by forcecore on 2012-05-27
Gnome Panel users please tell if you know what is this anomaly?

This panel interface is preferred by lot of people if i gave a choice which one you want: Unity or Gnome Panel and 75% picked panel that has been customized all in one by me (places and apps, window list, indicators and clock)

---

### Post by mc4man on 2012-05-27
I filed a bug on this over a year ago so the odds of getting 'fixed' are nil
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768)

What you can do is open any affected apps .desktop & either remove this line- 
StartupNotify=true
or edit to 
StartupNotify=false

So for nautilus, don't know which one the classic sessions so both - 
```
gksudo gedit /usr/share/applications/nautilus.desktop
```

```
gksudo gedit /usr/share/applications/nautilus-home.desktop
```

---

### Post by forcecore on 2012-05-28
Thank you so much, first line that helped already.

Ubuntu devs here is solution: just use default StartupNotify=false for panel and it is fixed simple as that.

---

### Post by VMC on 2012-06-05
I get something a tad bit different, but just as annoying.

When I open nautilus, my cursor becomes a "spinning wheel" and there's a "Staring Folder" icon at the bottom panel. This stays on for several seconds.

All the while, I can navigate or anything else in nautilus, but question what is causing this.

I should and may still open another thread, but was wondering if this is related to the topic at hand. I changed the "StartupNotify=false", but to no difference.

---

### Post by xpucto on 2013-01-26
> What you can do is open any affected apps .desktop & either remove this line- 
StartupNotify=true
or edit to 
StartupNotify=false

So for nautilus, don't know which one the classic sessions so both - 
```
sudo gedit /usr/share/applications/nautilus.desktop
``````
sudo gedit /usr/share/applications/nautilus-home.desktop
```

That fixed it for me.
Thank you very much.Finally,that annoying window is gone.I am using Gnome Classic if that matters.

---

### Post by vcrpcant on 2013-07-08
> **VMC said:**
> I get something a tad bit different, but just as annoying.

When I open nautilus, my cursor becomes a "spinning wheel" and there's a "Staring Folder" icon at the bottom panel. This stays on for several seconds.

All the while, I can navigate or anything else in nautilus, but question what is causing this.

I should and may still open another thread, but was wondering if this is related to the topic at hand. I changed the "StartupNotify=false", but to no difference.


Same happens to me :(
I've tried changing Nautilus config files line startupnotify from true to false, but no luck

I also think this isn't a Nautilus problem, because it also happens with Thunar

I'm on Ubuntu Desktop 12.04 64 bit Gnome Classic no effects

---

### Post by Traxster on 2013-07-14
> **mc4man said:**
> I filed a bug on this over a year ago so the odds of getting 'fixed' are nil
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768)

What you can do is open any affected apps .desktop & either remove this line- 
StartupNotify=true
or edit to 
StartupNotify=false

So for nautilus, don't know which one the classic sessions so both - 
```
sudo gedit /usr/share/applications/nautilus.desktop
```

```
sudo gedit /usr/share/applications/nautilus-home.desktop
```

wow, 

nice

no more spinning wheel for 20 seconds when you start up nautilus, by the way I am running Ubuntu 13.04 x64 Gnome, and this solved it for me.

---

### Post by VMC on 2013-07-14
> **mc4man said:**
> I filed a bug on this over a year ago so the odds of getting 'fixed' are nil
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768)

What you can do is open any **affected apps** .desktop & either remove this line- 
StartupNotify=true
or edit to 
StartupNotify=false

So for nautilus, don't know which one the classic sessions so both - 
```
sudo gedit /usr/share/applications/nautilus.desktop
```

```
sudo gedit /usr/share/applications/nautilus-home.desktop
```
It took me a while to figure this out. I missed the step about "affected apps", and just applied the 'false' to both the aforementioned nautilus files. Realizing that my "spinning wheel" is only involved using multiple gedit edits, I then applied 'false' to gedit.desktop. It now works as expected.

---

### Post by mc4man on 2013-07-14
Just to note - 
starting  in 13.04 users should no longer use sudo gedit, sudo nano or  gksudo gedit would be better. 
Overall they are moving away from gksu(do) & it's no longer default installed

Here I've switched over to enabling pkexec for both gedit & nautilus but that has not been done offically

---

### Post by VMC on 2013-07-14
First time I've seen pkexec ,so lets take a closer look at **[pkexec]("http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo")**. Interesting. Its always good to see the direction the boat is traveling. I'll have to keep a closer eye on this. I usually  use the "open-as-root", and then edit that way, but that requires another install.

edit: also the man pages are helpful on this command (or any command, for that matter).

---

### Post by mc4man on 2013-07-14
> **VMC said:**
> First time I've seen pkexec ,so lets take a closer look at **[pkexec]("http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo")**. Interesting. Its always good to see the direction the boat is traveling. I'll have to keep a closer eye on this. I usually  use the "open-as-root", and then edit that way, but that requires another install.

edit: also the man pages are helpful on this command (or any command, for that matter).

One of the issues with gksudo gedit prior to gedit 3.8 is it would try open a 2nd untitled window (bug never to fixed
That's why in past have suggested sudo gedit as it would not do that or create any other issue. 
Staring in 13.04 (or maybe 12.10) if one uses sudo gedit they'll notice gedit *now* uses the user's preferences rather than root's.

It was mentioned to me in 13.04 dev ( on my bug on the 2nd window) that pkexec would be the way but it hasn't been forthcoming.

I've got pkexc enabled builds of both gedit & nautilus in several ppa's but they're not just gedit & nautilus & also have some changes to nautilus so I don't particularly advertise them.
If nothing is forthcoming officially I may move them to a standalone ppa for just pkexec (precise, raring, saucy, the gedit I've redone for saucy also includes a built-in "geditas" extension I got from my friends at nautilus-actions ppa

Anyway it's pretty simple to add support to a current install - if there"s any interest will post instructions

---

