---
title: "Reverting back to default panels in Ubuntu 9.04"
date: 2009-05-15
forum: General Help
---

### Post by XMan75 on 2009-05-15
Slight newbie when it comes to Linux here, so bear with me if I ask a dumb question.



I'm using Ubuntu 9.04 with GNOME as my graphical interface. I had the default panels on my panel setup up top(or down below for some of you). Applications/System/Places, and then on the other side it had my battery indicator, wireless signal strength, time and a button for logging me out. These were the panels that came with 9.04. On accident, I clicked the "Delete Panel", misunderstanding what it did. My entire panel/toolbar disappeared and I'm having an impossible time repairing it. I tried using these codes:


rm -rf ~/.gconf/apps/panel



killall gnome-panel



And then hitting Alt+f2 and typing in gnome-panel as I found in this thread: 

[http://ubuntuforums.org/showthread.php?t=771660](http://ubuntuforums.org/showthread.php?t=771660)




Does anyone know how I can get the default panels back that came with 9.04 without redoing a fresh install of it? Thank you SO much.

---

### Post by Screwdriver0815 on 2009-05-15
what did you type then?

first you must type

```
rm -rf ~/.gconf/apps/panel
```

then 

```
killall gnome-panel
```

then

```
gnome-panel
```

if this does not work, just re-install the panels:

```
sudo apt-get install gnome-panel
```

if this doesn't work, maybe re-installing of gnome and the ubuntu desktop helps

```
sudo apt-get install gnome-core ubuntu-desktop
```

if there is a failuremessage that the package is defect or something, just use

```
sudo apt-get -f install 
```

instead of "apt-get" only, so just insert "-f install" additionally

hope this helps!

---

### Post by XMan75 on 2009-05-15
> **Screwdriver0815 said:**
> what did you type then?

first you must type

```
rm -rf ~/.gconf/apps/panel
```

then 

```
killall gnome-panel
```

then

```
gnome-panel
```





Those right there did work, actually. I failed to remember that I had to reboot my computer for it to take effect! Thank you SO much for the response! Ever since joining the Ubuntu users around the world in October, it's actually become my preferred OS of choice. I've not had to use a virus scanner once, or anything like that. Hail Ubuntu!

---

