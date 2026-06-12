---
title: "Upgrade to kde 4.4"
date: 2010-03-05
forum: Desktop Environments
---

### Post by inobe on 2010-03-05
has anyone been successful upgrading to kde 4.4 in kubuntu karmic, i borked the the system on the last attempt and needed to reinstall kubuntu desktop.


thanks for any tips.

---

### Post by Melcar on 2010-03-05
Yes, using the Kubuntu Backports repository.  But I think something got screwed during the update; kpackage kit no longer prompts for password (therefore I can't install things with it, though apt-get still works) and launching apps. with kdesudo causes a "protocol stopped responding" type error (depends on the application being launched, but usually it renders the app. useless).

---

### Post by inobe on 2010-03-05
got a krash dialog with a black background, nothing to do, couldn't envoke konsole or anything.


upgraded to 4.4 in opensuse, it went smoothly, figured why not upgrade in kubuntu too.

hoping i can find a solution and avoid another crash.

thanks

---

### Post by genux05 on 2010-03-05
what is the new things in kde 4.4 over 4.3.2 ? anything nice ?

---

### Post by wojox on 2010-03-05
I used this how to here and it worked real smooth: [http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml](http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml)  . 4.4 is pretty sweet. Never been a kde fan until this release.

---

### Post by inobe on 2010-03-05
there are thousands of bug fixes with almost 2000 new features.

[http://www.kde.org/announcements/4.4/](http://www.kde.org/announcements/4.4/)

i used this guide to upgrade kde in opensuse

[http://anl4u.com/?p=382](http://anl4u.com/?p=382)

i just need a decent guide for kubuntu.

---

### Post by inobe on 2010-03-05
> **wojox said:**
> I used this how to here and it worked real smooth: [http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml](http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml)  . 4.4 is pretty sweet. Never been a kde fan until this release.

i don't have gnome desktop, it's only kde, i use to switch environments at sessions select.

is there a section of that guide i should concentrate on, thank you

---

### Post by genux05 on 2010-03-05
It does look very nice..  and also looks it is coming with release lucid 10.04 :). so may just updated now to lucid testing and enjoy the show :)

---

### Post by wojox on 2010-03-05
Sure run this in your terminal:

```
sudo add-apt-repository ppa:kubuntu-ppa
```

Then:

```
sudo apt-get update && sudo apt-get dist-upgrade

```

---

### Post by inobe on 2010-03-06
> **wojox said:**
> Sure run this in your terminal:

```
sudo add-apt-repository ppa:kubuntu-ppa
```

Then:

```
sudo apt-get update && sudo apt-get dist-upgrade

```

thanks i will give it a go.


if all heck breaks loose i will provide some feedback.

---

