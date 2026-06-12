---
title: "Shortcut keys for workspace navigation not working"
date: 2014-01-09
forum: Desktop Environments
---

### Post by jaimeda104 on 2014-01-09
After making a fresh install of Ubuntu 13.10 Saucy Salamander I installed gnome fallback version because I like gnome classic. I was configuring like always and I realized that the regular shortcut for workspace navigation (Ctrl+Alt+Arrow) is not working. It is weird because my shortcuts for Terminal (Ctrl+Alt+t) and Dekstop (Ctrl+Alt+t) are working correctly. To try solving the problem I did the following:

1.-  I tried to see the Keyboard shortcut layout for navigation in System Settings. To my surprise they were configured correctly.
2.-  I used the CCSM to check the same thing and even though everything was somehow correct I got with the surprise that sometimes de Ctrl key is called Primary instead, changing the shortcuts here for Primary or Ctrl did not work in any case.
3.-  I used dconf-editor and went to org->gnome->desktop->wm->keybindings and same things as CCSM.

After this I read in some forums that maybe the problem is with the repository that the distro used for installing gnome-control-center or gnome-control-center-unity. I saw that many people got similar (not same) problems because of GNOME 3 PPA. In my case, as I did a fresh install, the result of the command: 

```
apt-cache policy gnome-control-center
```

is:

```
gnome-control-center:
  Installed: 1:3.6.3-0ubuntu45.2
  Candidate: 1:3.6.3-0ubuntu45.2
  Version table:
 *** 1:3.6.3-0ubuntu45.2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu44 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
```

So because of this I assume that the repos are correct and there should be no problem. Another thing (I am not sure if there is somethign related to this) is that I have no "Appearance" option in System Settings and that my FN key work for all keys but the numeric ones (numeric keyboard embedded in letters). I am not sure what else to do or check, is there someone else with my problem and maybe the solution to it? Thank you in advance.

---

### Post by jaimeda104 on 2014-01-09
Ok I noticed something even stranger, I tried to move an opened window to another workspace by hand and its impossible, even when the windows is half inside the first workspace it does no exist in the next one. Also if I click in another workspace using the applet in the panel and my mouse, in any other workspace if I open something it will open in the first workspace and return me there.

---

### Post by jaimeda104 on 2014-01-09
Ok somehow I solved my problem. I tried using ubuntu-tweak to see if the multiple workspace option was enabled. As I presumed it wasn't so I just enabled it and created a 2x2 arrange of workspaces. This did not work at all. Finally the solution was very simple, I entered the CCSM general options and in the Desktop Size tab even though the ubuntu-tweak and workspace applet were showing 4 workspaces with 2x2 arrangement, here I could only see 1 horizontal dekstop, nothing else. Redefining the number of dekstops and the horizontal and vertical arrangements there worked for me.

The other thing is that the Workspace Shifter (applet in panel) and compiz get confused with each other, to make them work together I had to configure compiz desktop size as I said before but change the configuration of the Workspace Shifter to: Number of workspaces = 1.

---

