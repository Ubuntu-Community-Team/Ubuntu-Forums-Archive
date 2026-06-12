---
title: "[SOLVED] Which firefox to keep?"
date: 2008-12-25
forum: Desktop Environments
---

### Post by Barriehie on 2008-12-25
I was noticing in synaptic that I've got firefox, firefox-2, and firefox-3.0.5 installed.  Seems like a lot so I did ```
which firefox
``` and got /usr/bin/firefox.  After that I did ```
ls -l /usr/bin/fire*
``` and got:

```

lrwxrwxrwx 1 root root 11 2008-12-20 07:49 ./firefox -> firefox-3.0
lrwxrwxrwx 1 root root 24 2008-12-20 07:57 ./firefox-2 -> ../lib/firefox/firefox-2
lrwxrwxrwx 1 root root 31 2008-12-20 07:57 ./firefox-3.0 -> ../lib/firefox-3.0.5/firefox.sh

```According to this it looks like I can remove firefox-2 and then make firefox link to the firefox.sh file???

Thanks People,
Barrie

Edit:  It just seems like firefox is getting 'windowfied' with the amount of updates/downloads it's requiring.  
         Last update time it needed 23 megs of whatever.

---

### Post by tank.null on 2008-12-25
you can try to fond out the package contain the file /usr/bin/firefox-2.

dpkg -S /usr/bin/firefox-2

and try to remove or reinstall firefox.

---

### Post by zrs_12 on 2008-12-25
What is the output of ```
sudo apt-get -s remove firefox*
```?

---

### Post by Barriehie on 2008-12-25
> **zrs_12 said:**
> What is the output of ```
sudo apt-get -s remove firefox*
```?

That will remove all of them :eek:  I went into synaptic and firefox-3 hasn't any dependencies on the -2 version and shows conflicts with <3 so,  when I'm done GIMP'ing I'll try removing the first two and change the launcher on the panel to point to 3.0.5 version.  I'll post back.

Thanks Guys!
Barrie

---

### Post by ugm6hr on 2008-12-25
> **Barriehie said:**
> That will remove all of them :eek: 

The "-s" option runs a simulation in apt-get; it won't remove anything

---

### Post by zrs_12 on 2008-12-25
No it won't.  The -s switch just gives a test of removing the package.

---

### Post by Barriehie on 2008-12-25
Okay, firefox is the 'main' part of the browser and points to whatever upgraded version you have so you have to keep that.  I removed firefox-2 and picked up 35 megs of drive space and only lost the icon on the panel.  No big deal, there's one in /usr/lib/firefox-3.0.5/icons that's working just fine.

Then I edited the launcher properties of the panel icon to point to the 3.0.5 version; previously it was pointing to firefox which was a link to 3.0.5 version.

Thanks all,
Barrie

---

