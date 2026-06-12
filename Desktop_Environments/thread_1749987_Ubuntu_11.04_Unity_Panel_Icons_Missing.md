---
title: "Ubuntu 11.04 Unity Panel Icons Missing"
date: 2011-05-05
forum: Desktop Environments
---

### Post by CaptainPasty on 2011-05-05
Just thought I'd post this incase it helps anybody...

After playing around with Ubuntu Tweaks to remove the "Recent Documents" logging, I somehow ended up losing the icons for "Applications" and "Files & Folders".

I tried lots of different things but the only thing that seemed to sort it was this:

Log out. Log in under Ubuntu Classic (for some reason dropping back to tty with Ctr, Alt and F2 didn't do it). Bring up the terminal and do

```
sudo apt-get purge unity
```Restart your machine

Log back into Ubuntu Classic and bring up the terminal again.

```
sudo apt-get install unity
```Restart again.

Log back into Ubuntu (not classic) and hopefully, you should end up with all icons back as they were.

This worked for me but I can't remember if I'd gotten rid of the ".recent-documents.xbel" file in my home folder first, so if all else fails you could try that before you start removing and re-installing Unity.

Anyway, hope it helps somebody.

---

### Post by GuiHarrison on 2011-05-07
Funny, I'm having the exact same problem but didn't seem to help. I restored the GNOME panel so I could star the  browser and look for a answer so, do you think this might be the cause of my unsuccess? Thanks anyway.

---

### Post by sirius56 on 2011-05-08
CaptainPasty, I tried your two suggested  terminal commands but still can't add any applets to my Unity panel.  Right-clicking on the panel area does nothing.  Applets are visible under Classic but not in Unity.

Has Unity disabled the Panel?

---

### Post by sree15081947 on 2011-05-10
dear all,

 this will help you, do the following.

go to console (alt+ctrl+f1/f2.....f6) and apply the command

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

after this restart your system.


this will solve the problem.

thanks............................

---

### Post by Krytarik on 2011-05-10
> **sree15081947 said:**
> dear all,

 this will help you, do the following.

go to console (alt+ctrl+f1/f2.....f6) and apply the command

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

after this restart your system.


this will solve the problem.

thanks............................
**You shouldn't do that unless you want to reset almost your entire Gnome/Unity environment and most of your apps!**

Greetings.

---

### Post by tedrogers on 2011-10-14
> **Krytarik said:**
> **You shouldn't do that unless you want to reset almost your entire Gnome/Unity environment and most of your apps!**

Greetings.

Hi there,

So what if I just want to refresh my icons? I'm missing my FPM2 icon, an app I use a lot, so I like it on the unity launcher. Right now I have a "?" where the icon was before upgrade from 11.04 to 11.10.

I used to do a "killall gnome-panel" for this sort of thing, but that's not going to work now is it?

This is bugging me. Please advise. Thank you.

---

### Post by Krytarik on 2011-10-14
> **tedrogers said:**
> I'm missing my FPM2 icon, an app I use a lot, so I like it on the unity launcher. Right now I have a "?" where the icon was before upgrade from 11.04 to 11.10.
This *generally* depends on:

[LIST=1]
[*]On what .desktop file your launcher is based.
[*]What icon image is specified in that .desktop file, if any.
[*]If that icon image is present in one of the various possible locations.
[/LIST]
However, I've learned that the handling of the launchers' icons can be weird and inconsistent in Unity at times, if I remember right.

---

### Post by tedrogers on 2011-10-15
> **Krytarik said:**
> This *generally* depends on:

[LIST=1]
[*]On what .desktop file your launcher is based.
[*]What icon image is specified in that .desktop file, if any.
[*]If that icon image is present in one of the various possible locations.
[/LIST]
However, I've learned that the handling of the launchers' icons can be weird and inconsistent in Unity at times, if I remember right.

Forgive my ignorance, but I don't know what a .desktop file is. Sure I have hidden files showing, but can't find a .desktop file anywhere. Where might I look to see where my icons are?

I'm also confused about Unity 2D / Unity (which is Unity 3D yes???). I've put ubuntu-desktop back on after it was auto-removed (by me). All the unity icons were huge, and I no longer had the Unity Plugin in CCSM in order to reduce the icon size. This is all very odd to get used to.

Thanks.

---

### Post by tedrogers on 2011-10-15
Okay, so I just fixed this:

I downloaded a suitable .png icon from the web, and placed it into the /usr/share/icons folder. Had to sudo it, but it worked, and when I next fired up FPM2 it must have checked the /usr/share/icons folder and rebuilt the icon in the Unity launcher. Nutty, but solved.

---

### Post by rkdn53 on 2011-11-04
I found a fix. 
I updated my Ubuntu 10.04 all the way to 11.10 thru the upgrades and after I did - my icons were missing in Unity
My Terminal icon, Home Icon and a few others. 
I tried making a few adjustments (compiz settings and gnome-tweak) but nothing worked. 
I finally ran>  sudo apt-get install ubuntu-desktop 
and it worked beautifully.

In 10.04 there were no missing icons and I was already using Gnome desktop. 
Not sure why but some of the files may have been deleted in the upgrades.

---

### Post by JamesFlamingo on 2011-11-22
An operating system without a functional start menu will never become popular.

---

### Post by JamesFlamingo on 2011-11-25
I read briefly that Oneiric [One-Eye-Rick] Ocelot has done away with the classic ubuntu menu. If this is true - i did not keep OO around longer than to find out that it was horrid - then Ubuntu has made the same mistake as Windows. I always used to have to switch back to classic from the day Vista showed up. I may have gotten used to doing without by the time Windows 7 came around. Anyway, to get rid of old menus when new ones are worse is apparently not an operating system problem. It is a problem with operating system designers instead, apparently. 

That said if you are in Natty Narwhal you can still use classic. I am learning how to add launchers to classic and it is not that hard. It looks more difficult with Unity. The reason is that the file association option seems to be slowly going away. In OO it very difficult to access. You cant get to it from the drop down menu. Still can in NN. That said there is something better. Often the application is not available in the list of the drop down menu for "use other application..." So there is no way to associate by checking "always use..."

I found that by clicking on "custom" there is a list of every app on the machine. This is great cause you can then associate the file with any app. AND better yet you can copy the custom command and go into the main memu [system setting>personal>main menu>add item>command] and paste the custom command in to create your own launcher which will show up (when checked) in the classic launcher. 

Hope this helps. Sorry for being so wordy. :o

---

### Post by arttymi on 2012-09-02
Worked for me too!!

QUOTE=CaptainPasty;10771879]

Log out. Log in under Ubuntu Classic (for some reason dropping back to tty with Ctr, Alt and F2 didn't do it). Bring up the terminal and do

```
sudo apt-get purge unity
```Restart your machine

Log back into Ubuntu Classic and bring up the terminal again.

```
sudo apt-get install unity
```Restart again.

Log back into Ubuntu (not classic) and hopefully, you should end up with all icons back as they were.

This worked for me but I can't remember if I'd gotten rid of the ".recent-documents.xbel" file in my home folder first, so if all else fails you could try that before you start removing and re-installing Unity.

Anyway, hope it helps somebody.[/QUOTE]

---

