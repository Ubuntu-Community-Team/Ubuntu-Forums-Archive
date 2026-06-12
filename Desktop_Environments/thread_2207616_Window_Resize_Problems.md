---
title: "Window Resize Problems"
date: 2014-02-24
forum: Desktop Environments
---

### Post by joshuamuth on 2014-02-24
I'm not sure what happened. I'm running 12.04 LTS and I used to have the option of dragging a window to the edge of the screen to re-size it to half the screen just like in windows 7. I updated some packages through the update manager and then after a restart when I tried to log in in it would say something like "Could not load session: ubuntu" then it would log me out. I fixed that problem by exiting to command line and installing the ubuntu desktop using these commands:
> [COLOR=#333333][FONT=UbuntuRegular]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install ubuntu-desktop[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install -f install[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo dpkg-reconfigure ubuntu-desktop[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo reboot[/FONT][/COLOR]
Now when I can log in, but I lost the ability to re-size the windows like windows 7 which sucks. Please help!!!

---

### Post by joshuamuth on 2014-02-24
I fixed it by updating to the latest amd apu drivers. I could have sworn I already had them but whatever.

---

