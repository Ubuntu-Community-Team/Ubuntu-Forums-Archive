---
title: "how do I install breezy from synaptic?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by tikal26 on 2005-10-07
:confused: hey:
I discovered KLinux and kubuntu a year ago i want to uprgrde to breezy now, but i am wondering how do I do it from synpatic. is there a way? or do I have to do it from the command line.
again thanks for all your help.

---

### Post by adwait on 2005-10-07
You could do it from synaptic......but it would be easier/faster do it via commandline. So unless you are really scared of the command line......here's how to do it:
Open the /etc/apt/sources.list file:
```
sudo gedit /etc/apt/sources.list
```

Now change all the hoary references to breezy (simply replace the word "hoary" with "breezy" everywhere you see it).

then run the following. I suggest that instead of running this in Konsole, run it in a virtual terminal....press Shit+Alt+F1 and login. Then enter these commands...
```
sudo apt-get update
sudo apt-get dist-upgrade

```

It will ask you some questions sometimes.......just accept the default by pressing enter. If anything goes wrong on the way, use:
```
sudo apt-get install -f
```

---

### Post by twoseids on 2005-10-07
[QUOTE=adwait]You could do it from synaptic......but it would be easier/faster do it via commandline. So unless you are really scared of the command line......here's how to do it:
Open the /etc/apt/sources.list file:
```
sudo gedit /etc/apt/sources.list
```

Now change all the hoary references to breezy (simply replace the word "hoary" with "breezy" everywhere you see it).

then run the following. I suggest that instead of running this in Konsole, run it in a virtual terminal....press Shit+Alt+F1 and login. Then enter these commands...
```
sudo apt-get update
sudo apt-get dist-upgrade

```

It will ask you some questions sometimes.......just accept the default by pressing enter. If anything goes wrong on the way, use:
```
sudo apt-get install -f
```[/QUOTE]
I have a related question: If I do it the way you suggest, will it wipe out all the Gnome stuff I have on my computer? I'm asking because I just recently switched to KDE (I'm a noob myself), and would like to just install Kubuntu minus all the Gnome default stuff.

Would I be better off just downloading Kubuntu off the web, burning it on a CD and then doing a fresh install of it? I have /home in a separate partition from root, so it shouldn't be a problem, right?

---

### Post by Velox Letum on 2005-10-07
You can just remove the GNOME stuff manually with Kynaptic, though I chose to keep Synaptic (a far superior program) and remove all except the GNOME and GTK libs, and installed this library call gtk2-engines-gtk-qt which with a few clicks in kcontrol had Synaptic, X-Chat, gaim, and more all looking just like my KDE theme.

---

### Post by tikal26 on 2005-10-07
ok so I did that but now i only get a text login and stuff no gui or kdm

---

### Post by Kapre on 2005-10-07
tikal26 - type "startx" and it will bring up the GUI.

K

---

### Post by tikal26 on 2005-10-08
ok so I think that I broke the system or something because I type startx and nothing so i tries
sudo init 1
sudo init 5
and then again startx
so I did this 
sudo dpkg-reconfigure -phigh xserver-xorg
and i get this error
pearl warining:setting locale failed
pearl warning: please check that your local setting:
Language= "en"
LC_ALL= (unset),
LANG = "eng_us.utf-8"
pear:l warning: Falling back to the standard local ("C") 
locale: cannot set LC_ctype to default locale: No such file or directory 
locale: cannot set LC_MESSAGES to default locale: No such file or directory 
locale: cannot set LC_All to default locale: No such file or directory

How do I check for my local settings?
any help would be apreciated

---

### Post by twoseids on 2005-10-08
Yeah - I think I'm just going to do a fresh install.  :^)

---

### Post by adwait on 2005-10-08
Like I said.........did you try
```
sudo apt-get install -f
```
I had such troubles after the upgrade as well........but the above command fixed most of them.

---

