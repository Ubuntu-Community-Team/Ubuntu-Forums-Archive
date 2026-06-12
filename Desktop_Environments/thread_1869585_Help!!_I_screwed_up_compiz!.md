---
title: "Help!! I screwed up compiz!"
date: 2011-10-26
forum: Desktop Environments
---

### Post by Risingfate on 2011-10-26
I have no idea what happened. But i was editing some settings in compiz and my computer froze completely and wouldn't let me click anything. I had to restart the computer manually. and when i logged back in my desktop looked like the picture below! No unity! No compiz! No way to even summon a terminal!
 
[ATTACH]205503[/ATTACH]
 
So I rebooted and logged in under ubuntu2d and everything worked fine. So i'm assuming it has something to do with the compiz/unity interface. But I have no idea where to look since i'm a huge noob :(
 
I tried resetting unity and compiz with "unity --reset" and another command. But that just hung and froze too :(
 
I have all of my files backed up on ubuntu one so it isn't a huge deal if i have to reinstall but I don't really want to make a new install disk for 11.10 (Since that's what I just upgraded to). I was considering just using unity2d or gnome shell anyway. So it isn't too terribly inconvenient but I thought it would be helpful to fix the problem and not just ignore it. Thanks!
 
Any help would be amazing!

---

### Post by remotusesse on 2011-10-26
I tried to use Cube desktop through Compiz and it screwed things up for me. I also could only use Ubuntu 2D. I logged into U2D and did the following

$ sudo apt-get remove --purge compiz* 
$ rm -rf .compiz-1
$ rm -rf .gconf/apps/compiz* 
$ sudo apt-get install compiz compiz-core
$ sudo apt-get install unity 

Things are working for me again, hope this helps.

---

### Post by Risingfate on 2011-10-26
I tried that and no luck :( I still get the same thing! Thanks for the quick reply though!

Anyone else?

---

### Post by Copper Bezel on 2011-10-26
Purging Compiz won't remove the settings that it stores in gconf (similar to Windows' "registry".) Run these instead from your Unity 2D session, then try logging into the normal one.

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
```

This is from Tux Garage, which has [_a troubleshooting guide_]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") for some other possible problems, but I think this is the one you have.

---

### Post by typhoon_tip on 2011-10-26
No need to be so drastic with re-install everything ! If you are able to manage somehow to open ccsm (terminal command: ccsm) in your 3D Unity environment again, simply enable the Unity plugin back, it was surely switched off accidentally.

EDIT: the above reset of Compiz first might help !

---

### Post by Risingfate on 2011-10-29
Somehow i unlicked unity :)
 
Oops! Thanks so much!

---

