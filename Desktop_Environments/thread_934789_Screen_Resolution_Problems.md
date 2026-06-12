---
title: "Screen Resolution Problems"
date: 2008-10-01
forum: Desktop Environments
---

### Post by bwehrspann on 2008-10-01
Hello-

I would like a better screen resolution than 800x600 or 640x400

How do I get those choices to come up on screen resolution?

---

### Post by WWSmith36 on 2008-10-01
To increase you screen resolution you can use a tool to change your xserver setting like your video card driver and monitor. The tool is called displayconfig-gtk.

If displayconfig-gtk is not install you can install by typing

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk

```
Open a terminal from the menu Applications->Accessories->Terminal and type

```
sudo displayconfig-gtk
```

Try to configure your monitor to get more resolutions. You can select your monitor from the list or try to add it with the inf file from monitor driver cd, disk, or download.

After configuring you should reboot

Hope this helps

---

### Post by joseph2008 on 2008-10-01
This could be the result of a couple problems. The most likely problem is that your screen resolution is set too low.The whole problem is the difference between what resolution your monitor set.
___________________________________________________________
[promotional items](http://www.ideasbynet.com/promotional-items.htm) [Tail Lights](http://www.andysautosport.com/euro_tail_lights.html) [perfume store](http://www.eperfumestore.com/) [Sexual Predator List](http://www.registeredsexualpredators.org)

---

