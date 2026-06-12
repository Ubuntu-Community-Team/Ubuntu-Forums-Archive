---
title: "Gnome gui issue"
date: 2018-08-09
forum: Desktop Environments
---

### Post by ravensm on 2018-08-09
Slightly annoying problem. Gnome top menu is missing. Right now I'm missing Ubuntu GUI for all my needs, but would prefer Gnome.

Not sure how to trouble shoot this issue as I'm a new Linux user.

---

### Post by ajgreeny on 2018-08-09
I'm not sure what you mean by your question; what menu exactly are you not seeing?

The new ubuntu gnome GUI does not use a standard menu by default; it has an overview of applications installed if you click on the 9-dot icon bottom-left of the screen, or is that what's missing?
I think there is also a menu extension that can be enabled, perhaps after installing it first, using ubuntu-tweak but I do not use Ubuntu, preferring Xubuntu's classic GUI so I could be wrong about that.

---

### Post by ravensm on 2018-08-09
when i installed ubuntu gamepack 16.04, it had two different gui's one which was called ubuntu..the one your talking about, probbaly a version of gnome, but the os also had a straight up gnome gui, two menu bars, one on top and one on the bottom, i installed gnome twitch, and then restarted. when ht desktop came back up. the top menu was gone. i could access everything through terminal code commands, but the gui interface is basicly disabled. right now im using the ubuntu gnome gui, which is pretty and conveniant, but the regular gnome gui has a couple features which i kinda like and cause of that, i am hoping to get that gui working again

---

### Post by Frogs Hair on 2018-08-09
Ubuntu game pack is an operating based on Ubuntu, so may not have the same GUI options as official Ubuntu. Not sure if they can legally use the  Ubuntu name without official flavor status.  

[https://ualinux.com/en/ubuntu-gamepack](https://ualinux.com/en/ubuntu-gamepack)

---

### Post by ravensm on 2018-08-09
its on this page  [https://ualinux.com/en/ubuntu-gamepack](https://ualinux.com/en/ubuntu-gamepack)   ...anyways. all that is besides the point. look i had two menus, one on top and one on the bottom, the discription is all over the net. im not talking about the gui with the pretty toolbar on the left..im talking about a different gui  

[https://www.gnome-look.org/p/1080260/](https://www.gnome-look.org/p/1080260/)

this is the gui im talking about. when i log off, and go to log back on, i have an option to pick this gui or this one

[https://comtechies.com/how-to-set-up-gui-on-amazon-ec2-ubuntu-server.html](https://comtechies.com/how-to-set-up-gui-on-amazon-ec2-ubuntu-server.html)

sighs, the frustrating thing is i explained all this. the topic was to help me get my tool bar back, not discuss who made what linux distro and whether or not is legal

edit - - just looked at my original post and i did say missing by accident, ment to say i've been using a different gui till i get my problem fixed. anyways, my second post explains my problem a lot better

---

### Post by oldfred on 2018-08-10
I am using gnome-panel, but it may be bungie or Mate.
[https://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](https://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available)

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

       Or, if you're running either Ubuntu or Ubuntu GNOME you can install 'gnome-panel' which will provide GNOME Flashback session(s). The Flashback w/Metacity session is fairly comparable to MATE w/Marco in resource usage. 
    
I have always run gnome-panel/fallback/flashback even though name has changed. Originally somewhat like Mint as based on gnome3, but updated to gnome3 with old gnome2 top & bottom panels.

If you have multiple desktops installed, you choose which to use when logging in. There is a small gear/star icon which when clicked will show what other sessions you have available.

---

### Post by Frogs Hair on 2018-08-10
> **ravensm said:**
> its on this page  [https://ualinux.com/en/ubuntu-gamepack](https://ualinux.com/en/ubuntu-gamepack)   ...anyways. all that is besides the point. look i had two menus, one on top and one on the bottom, the discription is all over the net. im not talking about the gui with the pretty toolbar on the left..im talking about a different gui  

[https://www.gnome-look.org/p/1080260/](https://www.gnome-look.org/p/1080260/)

this is the gui im talking about. when i log off, and go to log back on, i have an option to pick this gui or this one

[https://comtechies.com/how-to-set-up-gui-on-amazon-ec2-ubuntu-server.html](https://comtechies.com/how-to-set-up-gui-on-amazon-ec2-ubuntu-server.html)

sighs, the frustrating thing is i explained all this. the topic was to help me get my tool bar back, not discuss who made what linux distro and whether or not is legal

edit - - just looked at my original post and i did say missing by accident, ment to say i've been using a different gui till i get my problem fixed. anyways, my second post explains my problem a lot better

What they refer to as Ubuntu OEM of which game-pack is based on does offer Gnome Flashback which is what I think you may have seen. As I wrote they do offer different GUI options than Ubuntu. To find out what session is in use use the following command.```
echo $XDG_CURRENT_DESKTOP
```


> [COLOR=#0F1419][FONT=Ubuntu]We offer distributions **Ubuntu*Pack** with various embodiments of user interfaces:

**Unity** - universal interface from the company Canonical, optimized for computers and tablets
**Flashback** - classical view desktop style in GNOME 2 to GNOME 3 libraries
**GNOME** - universal interface for computers and tablets. His other names - GNOME 3 and GNOME Shell
**GNOME 3 Classic** - version of the classic representation of the GNOME 2 desktop in the GNOME 3 style
**Cinnamon** - close to the style of the interface **Windows** uses GNOME 3
**MATE** - further development of the classic GNOME 2 interface, works well on **low-end PCs**[/FONT][/COLOR]



---

### Post by ravensm on 2018-08-10
using that code, the desktop im having issues with is:
GNOME-Flashback:Unity

because of the top menu bar being disabled for some odd reason, or missing. im using a desktop that shows up as "Unity" when entering that code.

i cant even log out unless i use the terminal

---

### Post by ravensm on 2018-08-10
oh and just so everyone knows, i didnt add these gui's to my linux, ubuntu gamepack 16.04 came with these pre installed

---

### Post by Frogs Hair on 2018-08-10
Do you have have access to the screen-shot tool ? If so upload a screenshot using the paper clip attachment tool above the reply box . In the mean time I'll look for info on resetting the flashback session.

This a terminal command used to reset the panel in the flashback session. 

```
dconf reset -f /org/gnome/gnome-panel
```

---

### Post by ravensm on 2018-08-10
[https://imgur.com/a/VvSZpn1](https://imgur.com/a/VvSZpn1)

---

### Post by Frogs Hair on 2018-08-10
Looks like the flashback session. Did you try the command ?

  
```
dconf reset -f /org/gnome/gnome-panel
```

---

### Post by ravensm on 2018-08-10
[https://imgur.com/E9AfJ5K](https://imgur.com/E9AfJ5K)

that code didnt seem to do anything

anyways, that link will take you to a screen shot of my desktop

---

### Post by ravensm on 2018-08-10
its the flashback gui, as you can see, the top menu which is where i access all my apps is gone

---

### Post by Frogs Hair on 2018-08-10
> **ravensm said:**
> [https://imgur.com/E9AfJ5K](https://imgur.com/E9AfJ5K)

that code didnt seem to do anything

anyways, that link will take you to a screen shot of my desktop

Have to keep looking then , I think that having multiple session available may complicate matters.

---

### Post by ravensm on 2018-08-10
that could be it, but these sessions where pre installed so im not sure how to go about removing them. theres cinnamon, 2 flashbacks, ubuntu which is unity. um..one more i think

---

### Post by Frogs Hair on 2018-08-10
Another variant of the command to try.

```
dconf reset -f /org/gnome/gnome-panel/killall gnome-panel
```

---

### Post by Frogs Hair on 2018-08-10
> that could be it, but these sessions where pre installed so im not sure  how to go about removing them. theres cinnamon, 2 flashbacks, ubuntu  which is unity. um..one more i think 				

I would leave them for now. There are two flashback sessions, one that uses compiz and one that's matacity only. Cinnamon is native to mint though available in Ununtu.

---

### Post by ravensm on 2018-08-10
i tried that code but it didnt do anything. i do have to say that this all happened after i installed gnome twtich. which actually doesnt seem to work.

---

### Post by Frogs Hair on 2018-08-10
> **ravensm said:**
> i tried that code but it didnt do anything. i do have to say that this all happened after i installed gnome twtich. which actually doesnt seem to work.

If it's not working try removing the application and restarting.

---

### Post by ravensm on 2018-08-10
gnome-twitch is now gone and i restarted the pc, but the toolbar still isnt working

---

### Post by Frogs Hair on 2018-08-10
Try the last command I posted one last time.

---

### Post by ravensm on 2018-08-10
still no luck, sorry

---

### Post by Frogs Hair on 2018-08-12
Try the following.

```
sudo apt install dconf-editor
``` 

```
dconf reset -f /org/gnome/gnome-panel/killall gnome-panel
```

---

