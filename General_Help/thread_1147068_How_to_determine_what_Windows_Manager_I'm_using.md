---
title: "How to determine what Windows Manager I'm using?"
date: 2009-05-03
forum: General Help
---

### Post by techphets on 2009-05-03
I'd like to learn more about my Windows Manager effects and characteristics but I keep getting stuck at step one: I don't even know which WM I'm using. 

I've read so many different things.  Metacity?  Compwiz?  Beryl?  

I installed Emerald.  That's about as far as I've gotten.  Now when I alt-tab between windows I get a nifty effect. 

I was hoping to see all the effects described on Beryl's page [here]("http://www.beryl-project.org/features.php").  Then I'm hoping to try out other WMs to find one I like. 

Particularly, one which allows me to double left-click the top left corner of a window to close it since I've been doing that in Windows for years.  

I installed Ubuntu but have since switched to KDE.  

I'm not sure where to find these menus in KDE:

System -> Preferences -> Advanced Desktop Effects Settings -> Rotate Cube

System -> Preferences -> Visual Effect


techphets

---

### Post by delcypher on 2009-05-03
There is a nifty program for switching between window managers called
fusion-icon.

```
sudo apt-get install fusion-icon
```

Then press [ALT]+[F2] and type fusion-icon, a small blue box icon should appear on KDE's application bar that allows you to switch between window managers.

As for controlling effects (assuming you use compiz) then ```
sudo apt-get install simple-ccsm
``` will install a compiz configuration manager that gives you plenty of control.

I've only ever tried this in GNOME so I don't know if this will work in KDE. Always worth a try though.

---

