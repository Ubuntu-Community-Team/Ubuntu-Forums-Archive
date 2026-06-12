---
title: "Install KDE4 in Ubuntu: directions confuse me."
date: 2007-12-11
forum: Desktop Environments
---

### Post by SomeGuyDude on 2007-12-11
Looking at the directions here: [http://www.kubuntu.org/announcements/kde4-rc1.php](http://www.kubuntu.org/announcements/kde4-rc1.php)

Now I'm just about as ultra-newbie as it gets with Linux, so you'll have to bear with me, but I don't get what this entire section means:

> # These KDE 4 packages install to /usr/lib/kde4 so run:

    * export LD_LIBRARY_PATH=/usr/lib/kde4/lib
    * export KDEDIRS=/usr/lib/kde4
    * export PATH=/usr/lib/kde4/bin/:$PATH
    * export KDEHOME=~/.kde4

# Run some programmes. Most parts run successfully.
# To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.
# To run it as a full session install kdm-kde4 and copy /usr/lib/kde4/share/kde4/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.

Obviously I can just use synaptic to install the packages in the first three steps, but what the heck does the rest of this mean? When it says "run" do I use the alt+F2 prompt for each? Can I get a breakdown of the last step?

Sorry if this is all obvious stuff, I'm just finding myself a little in over my head.

---

### Post by blazercist on 2007-12-11
i think you can just paste "export blah blah blah" to console each time and hit enter.  make sure to leave out the *'s

---

### Post by MetalMusicAddict on 2007-12-11
Just download and play with the [live disk]("http://kubuntu.org/~jriddell/cds/kubuntu-kde4-20071126.iso"). Its REALLY not worth installing.

---

### Post by firephoto on 2007-12-11
rc2 is out jfyi.

[http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php)

> # To run it as a full session install kdm-kde4 and copy /usr/lib/kde4/share/kde4/apps/kdm/sessions/kde.des ktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.
This is what I do, just follow what it says literally and you should get a "KDE 4" option in your login manager.

```

sudo cp /usr/lib/kde4/share/kde4/apps/kdm/sessions/kde.desktop /usr/share/xsessions/kde4.desktop
sudo nano -w /usr/share/xsessions/kde4.desktop
# edit the Name line and make it look like "Name=KDE 4" without the quotes.
sudo nano -w /usr/lib/kde4/bin/startkde
# copy the 4 export lines to the beggining of the file.

```
That's it, log out or start a new session. You might want to create a new user too in case the apps you run want to touch some of your existing kde3 data.

---

### Post by SomeGuyDude on 2007-12-11
> **MetalMusicAddict said:**
> Just download and play with the [live disk]("http://kubuntu.org/~jriddell/cds/kubuntu-kde4-20071126.iso"). Its REALLY not worth installing.

Isn't the live disk going to look and feel completely different than when it's on Ubuntu, though?

---

### Post by MetalMusicAddict on 2007-12-11
> **SomeGuyDude said:**
> Isn't the live disk going to look and feel completely different than when it's on Ubuntu, though?

No. They look the same and you really cant do much. Trust me. I'm close to the developers. Its just to tinker with.

---

### Post by SomeGuyDude on 2007-12-11
> **MetalMusicAddict said:**
> No. They look the same and you really cant do much. Trust me. I'm close to the developers. Its just to tinker with.

Kind of a crappy release candidate then, isn't it? Sounds more like a beta if it's just to tinker with and you can't do much with it.

---

### Post by firephoto on 2007-12-11
I think he was referring to the livedisk... and there's no lack of things to do.

I think running it with the livedisk is better anyway since there's some conflicts on a gutsy system unless you remove some of the qt4 things like strigi. I've been keeping up to date from svn for a few weeks now and it's running pretty good.

---

### Post by adityakavoor on 2007-12-11
I think LIVE disk wud be a better  option

---

### Post by exactopposite on 2007-12-11
> **firephoto said:**
> rc2 is out jfyi.

[http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php)


This is what I do, just follow what it says literally and you should get a "KDE 4" option in your login manager.

```

sudo cp /usr/lib/kde4/share/kde4/apps/kdm/sessions/kde.desktop /usr/share/xsessions/kde4.desktop
sudo nano -w /usr/share/xsessions/kde4.desktop
# edit the Name line and make it look like "Name=KDE 4" without the quotes.
sudo nano -w /usr/lib/kde4/bin/startkde
# copy the 4 export lines to the beggining of the file.

```
That's it, log out or start a new session. You might want to create a new user too in case the apps you run want to touch some of your existing kde3 data.

this worked fine for me. thaks for this.
looks like i'll be going back to kde full time when the final is released.

---

### Post by SomeGuyDude on 2007-12-12
Looks like with RC2 you don't need the fancy instructions, just install the repos and you're good to go. Score!

EDIT: Apparently not. I got a huge effing error, but I lost it. Some package conflict. I uninstalled what I could. Hm.

---

### Post by undine on 2007-12-12
> **SomeGuyDude said:**
> Looks like with RC2 you don't need the fancy instructions, just install the repos and you're good to go. Score!

EDIT: Apparently not. I got a huge effing error, but I lost it. Some package conflict. I uninstalled what I could. Hm.

sudo apt-get -f dist-upgrade fixes this problem, but then you run into other problems once you actually load the DE. There's no kicker to speak of, the system settings dialogue won't load, and the oxygen theme isn't utilised. Another crappy release, despite the claim that this is the last mile on the road to final release.

---

### Post by lexxonnet on 2007-12-12
Well, I just used the Opensuse live cd, and the release isn't nearly as bad as the kubuntu packages. TBH, Its not KDE thats at fault, its Kubuntu's packages. However, that said, this release does feel like the final beta, rather than the final release candidate.

Btw... I got the desktop working with Kubuntu, including panel and all, but there was a major conflict with kdesktop in kde3, especially having to replace one of its files. To get past that, I had to force dpkg to install over kdesktop, and then reinstall kdesktop after that.

---

### Post by firephoto on 2007-12-12
The panel with kickoff,  the system tray, the running tasks, a clock and even a media notifier all are working fine with a build from svn so there's either something wrong with the kubuntu builds or they are using old settings you had from previous tries.

I'm building from kdesupport up and uninstalled anything that it provides but everything else is regular ubuntu gutsy packages for dependencies.

---

