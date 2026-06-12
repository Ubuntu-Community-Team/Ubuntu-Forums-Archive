---
title: "Desktop not repainted when VLC exits"
date: 2010-09-08
forum: Desktop Environments
---

### Post by jay214128 on 2010-09-08
I'm running VLC (full screen mode) on Ubuntu 10.04 with the gnome desktop. When I exit from VLC, it does not repaint the desktop. It leaves the entire screen white. I can click on the screen, and this causes the rectangle formed by the upper left corner of the screen and the current mouse position to get repainted. So, by clicking on the screen near the bottom right corner will repaint the desktop (mostly). Does anyone know how to fix this?  I asked on the VLC forum, but they redirected me here.

---

### Post by TwelveGauge on 2010-09-08
VLC 1.0.6 is outdated for 10.04 and because of that there are some issues. This could be one of them, I don't know, I don't use it. HOWEVER, it could also be the result of an improper install or it could be a video problem. I suggest a reinstall before anything else. 

Remove VLC using Synaptic.

Then start from the beginning and check your repositories (for what it's worth)

Make sure you have whatever repositories you want set up properly:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
(so you have a backup in case things go awry

```
sudo gedit /etc/apt/sources.list
```
make sure that universe and/or multiverse repositories are uncommented (not that I think this is likely to be the problem but it never hurts to cover everything) If they are then close it, and move on. If they are not (if they still have the '#' in front of them, remove that and save. 

next:
```
sudo apt-get update
```

then:
```
sudo apt-get install vlc vlc-plugin-pulse
```
That should install VLC. I **do not** recommend the mozilla (firefox) plugin. 

Lemme know how this goes. (If you were watching VLC full screen in Firefox that could be your problem)

---

### Post by jay214128 on 2010-09-15
Well I tried the suggested options, but it made no difference.  I am not using VLC from Firefox (I don't even have the plugin installed).  I am using VLC in full screen mode.

Jay

---

