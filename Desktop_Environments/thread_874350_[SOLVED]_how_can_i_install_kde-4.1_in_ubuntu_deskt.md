---
title: "[SOLVED] how can i install kde-4.1 in ubuntu desktop?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by ramaswamyps on 2008-07-29
i already have ubuntu kde-3.5.9 all updated.
how can i try kde-4.1?
i dont want to install kubuntu desktop

---

### Post by gmoney on 2008-07-29
You may find this post helpful:

[http://kubuntuforums.net/forums/index.php?topic=3096395](http://kubuntuforums.net/forums/index.php?topic=3096395)

I haven't personally tried KDE 4.1, but I was really excited to hear about its release today.  I hope that guide works for you.  KDE 4.1 looks awesome, and they appear to have made a lot of improvements since the initial 4.0 release.  Let me know how you like it.

Also, if anyone is reading this post who is currently running gnome, but wants to try out KDE 4.1, here's an in depth guide:

[http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

---

### Post by ramaswamyps on 2008-07-29
from kubuntu.org i added the repo to sources.list
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

and apt-get update
apt-get upgrade brings in kde-4.1 some packages.upgrading kde-3.5.9
we willl know in an hour what happens.
i have tried kde-4.0.5 in gentoo. it was working good.
except the panel is not configurable.
let us see what is new in 4.1
in gentoo i could use both 3.5 and 4.0.5 in 2 slots.
here i will lose the kde-3.5.9 which is real stable kde.
:)

---

### Post by ramaswamyps on 2008-07-29
it downloaded some 60mb of files of kde-4.1 and after installing i do not find any trace of it.
even after restarting kde-3.5.9 is only showing up.
what happened to new installed packages?
dont understand what is happening here .:(

---

### Post by kuja on 2008-07-29
**ramaswamyps:** you need to install the **kubuntu-kde4-desktop** package.

---

### Post by gmoney on 2008-07-29
What happens when you click on help > about in a kde application (like dolphin or konqueror)?  It should show the KDE version you're running.  Is it still 3.5.9, or does it list 4.1?  I have a hunch it still says 3.5.9.

I noticed you ran 
```
apt-get update
```
```
apt-get upgrade
```

I re-read that Kubuntu Forum post I linked to in my first message.  That user ran:

```
apt-get update
```
```
apt-get dist-upgrade
```

Also, that post says something about dependency errors.  If you get any of those, run:
```
apt-get -f install
```

It seems like the upgrade you ran upgraded some of the applications, but not KDE itself.

---

### Post by ramaswamyps on 2008-07-29
distro upgrade will change ubuntu to kubuntu desktop
which i dont want to do.
i did not get any errors during apt-get uprade.
but now again i tried with synaptic mark all upgrades are fetching some more qt4 related packages.
may be this time i will get kde-4.1 desktop.
kubuntu is different from ubuntu desktop and various changes will happen to installed packages.
now what ever ubuntu kde can handle only being installed i hope.
will get back here as soon as synaptic completes the job.
thanks for support

---

### Post by ramaswamyps on 2008-07-30
by this exercise i got only konsole-kde-4.1
all others are kde-3.5.9
now i have marked upgrade of kde environment  
which downloads 169 packages.of kde4 .
it calls itself kde environment 3.3.
dont know what it means.
any way it all comes from kde-4.1 packages repo of Oubuntu1-Hardy1-ppa1
we will know in about 1 1/2 hours.
waiting for download to finish:)

---

### Post by ramaswamyps on 2008-07-30
yes kde-4.1 installed.
kdm still shows option for kde previous also
may be both versions of kde will work.
kde-4.1 screenshot i have posted for ref.
[http://omploader.org/vbjB6/kde-4http://omploader.org/vbjB6/kde-4](http://omploader.org/vbjB6/kde-4http://omploader.org/vbjB6/kde-4)

i find kde-3.5.9 also work fine.

---

