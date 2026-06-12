---
title: "screenlets didn't run"
date: 2009-07-02
forum: Desktop Environments
---

### Post by noiz354 on 2009-07-02
please help me
screenlets didn't run; 

when i run it from terminal it got this
> norman@norman-desktop:~$ screenlets-manager 
python: can't open file '/usr/share/screenlets-manager/screenlets-manager.py': [Errno 2] No such file or directory
norman@norman-desktop:~$ screenlets
python: can't open file '/usr/share/screenlets-manager/screenlets-manager.py': [Errno 2] No such file or directory
norman@norman-desktop:~$ screen
screen                  screenletsd             screen-profiles
screendump              screenlets-daemon       screen-profiles-export
screen-launcher         screenlets-manager      screen-profiles-status
screenlets              screenlets-packager     screen.real
norman@norman-desktop:~$ screenlets-packager 
python: can't open file '/usr/share/screenlets-manager/screenlets-packager.py': [Errno 2] No such file or directorythnx for advanced 
thnx for helping;)

---

### Post by Mia1990 on 2009-07-03
how did you install them from synaptic or the terminal i would say reinstall there is no directory for them

sudo apt-get install screenlets

---

