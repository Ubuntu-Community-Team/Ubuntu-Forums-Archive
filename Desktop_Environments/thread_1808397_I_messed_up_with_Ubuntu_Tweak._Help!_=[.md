---
title: "I messed up with Ubuntu Tweak. Help! =["
date: 2011-07-20
forum: Desktop Environments
---

### Post by Oodles on 2011-07-20
I was changing my menu button image using Ubuntu Tweak when it got stuck with EasyPeasy's lemon image. I've tried restoring my panel to default, and the lemon was still my default. I've taken away the original lemon file from its folder and it's still the lemon. I've also tried using gconf-editor to no success. I ended up deleting Ubuntu Tweak, and I still have the lemon.

(I was trying to change the logo to make it smaller than 22 pixels so that I can make my panel 18 pixels small, so I was doing a little trial-and-error with the icons in /usr/share/icons/. I thought the lemon in /usr/share/easypeasy/ would be smaller than those in the icons folder, and when I tested it out, it stuck.)

I had the idea of re-installing the Humanity-Dark theme to get my Ubuntu start-here.svg default back, but I don't even know how to install a .tar.gz.

Someone help me, please? =[
Thanks - in advance.

---

### Post by jerrrys on 2011-07-20
to install a tar file just double click on it, then extract

also a good idea to put it with the rest of them in:

/user/share/icons

---

### Post by Oodles on 2011-07-20
> **jerrrys said:**
> to install a tar file just double click on it, then extract

also a good idea to put it with the rest of them in:

/user/share/icons

I tried it, and the huge blasted yellow lemon is still there. =[
Thanks for the tip though. Dumping stuff in the root was a bit scary, but I now have a new set of icons. Haha.

I'm still wondering why or how the lemon got stuck there. Isn't Ubuntu Tweak supposed to fix that? =/

---

### Post by Oodles on 2011-07-20
Okay, so it looks like I've managed to somewhat solve my own problem. Remember how I uninstalled Ubuntu Tweak? I've reinstalled it, tried to revert my icon again, and it FINALLY DID! Yeeeeyyy!! Now I fiddled with it again to replace my current icon to a greyer version so that it's not as white by using the Humanity start-here.svg instead. AND IT WOOOORRKKKSSS. =D

Now I know not to just fiddle around too many times. xD

But if anyone knows what happened, please share. It may be a bug with Ubuntu Tweak for all I know, but if it happens to someone else, we could help. =D

---

### Post by drs305 on 2011-07-20
I just played with Ubuntu Tweak in a VM. When I changed the menu logo, it copied the selected icon to ~/.icons/<theme-name>/apps/24/start-here.png

After I did this, in the same Ubuntu Tweak page I set it, there was now a REVERT button which changed it back. This action removed the 'start-here.png' file in my .icons folder. 

In the future, if your problem repeats  and you don't get a REVERT button or it doesn't work, you could try to manually remove the start-here.png image from the appropriate ~/.icons folder.

---

### Post by Tornikee on 2012-02-15
I have another question regarding Ubuntu Tweak, and to save forums from a new thread, will post it here: how can I install icon themes via Tweak? Couldn't find relating menu.

---

### Post by Frogs Hair on 2012-02-15
You can change icon themes with Ubuntu Tweak via the theme settings , but you can't install them . 

(install Downloaded Themes or icons in 11.10)

Download and fully extract the theme packages and hold the folders on the desktop until needed . 

Install the Gnome Tweak Tool / Advanced Settings for making theme or icon selections from the software center .  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open the Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before theme are visible in Advanced Settings .  Ubuntu Tweak can be used to change themes or icons also , but Advanced Settings still needs to be installed .

---

### Post by Tornikee on 2012-02-15
> **Frogs Hair said:**
> You can change icon themes with Ubuntu Tweak via the theme settings , but you can't install them . 

(install Downloaded Themes or icons in 11.10)

Download and fully extract the theme packages and hold the folders on the desktop until needed . 

Install the Gnome Tweak Tool / Advanced Settings for making theme or icon selections from the software center .  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open the Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before theme are visible in Advanced Settings .  Ubuntu Tweak can be used to change themes or icons also , but Advanced Settings still needs to be installed .
Yeah I do have GNOME Tweak Tool and know how to do it there. Thanks anyways.

---

