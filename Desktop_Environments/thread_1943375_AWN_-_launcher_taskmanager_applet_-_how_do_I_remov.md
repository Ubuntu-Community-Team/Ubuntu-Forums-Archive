---
title: "AWN - launcher taskmanager applet - how do I remove the green + sign on the launcher?"
date: 2012-03-19
forum: Desktop Environments
---

### Post by miatawnt2b on 2012-03-19
I have AWN installed on 2 laptops, 0.4.0-2 on one and 0.4.1 on the other. The one running 4.1 has this goofy green 'plus' icon for the launcher applet in addition to all of my launchers. How do I get rid of it?  As far as I can tell, both are set up the same, yet the older version doesn't have this separate icon.
Thanks!
-J

---

### Post by Frogs Hair on 2012-03-19
Launchers can normally be removed with a right click or from the task manager settings by deleting it from the list. 

If it is an applet look in the applet settings and on the bottom select the icon and use the up arrow to remove any applets you don't want.

The settings icon will appear at one end of the dock and can be removed you just have right click the dock to get into Awn settings.

---

### Post by miatawnt2b on 2012-03-20
> **Frogs Hair said:**
> Launchers can normally be removed with a right click or from the task manager settings by deleting it from the list. 

If it is an applet look in the applet settings and on the bottom select the icon and use the up arrow to remove any applets you don't want.

The settings icon will appear at one end of the dock and can be removed you just have right click the dock to get into Awn settings.

the problem is that if I remove the launcher/taskmanager applet from the active applets, not only does the + icon go away, but so do all my launchers.

-J

---

### Post by Adam_GUI on 2012-03-22
I just did an upgrade to xubuntu 12.04 beta.
Running avant-window-navigator 0.4.1.

I, too, have this seemingly useless green plus sign.
Clicking on the plus sign does nothing.
Right-clicking the plus sign does nothing.  Not even options.

The applet menu makes no mention of a green plus.
It looks like it was tacked on to the launchers menu as a visual indicator that you can drag icons into the dash/add launchers to your liking.
Only, it never goes away.

I guess I can live with a dummy icon.  It's just kind of annoying.

---

### Post by Frogs Hair on 2012-03-22
I don't know what the plus is . I was trying the latest Awn from the software center over last weekend and didn't see what you are describing. I am using 11.10 .

---

### Post by miatawnt2b on 2012-03-22
Im actually having another problem too. AWN shows running applications fi something is open (say a terminal)

If multiple terminal windows are open, I can click on the icon in the AWN dock and it will list the active terminals. The problem comes when I move the mouse into the 'balloon" the bloon list disappears. I am running gnome-session desktop, but I have noticed the bug in the past running classic with compiz.

-J

---

### Post by Adam_GUI on 2012-03-22
> **Frogs Hair said:**
> I don't know what the plus is . I was trying the latest Awn from the software center over last weekend and didn't see what you are describing. I am using 11.10 .

Right between the VLC traffic cone and the file manager windows.

---

### Post by miatawnt2b on 2012-03-22
I just switched to cairo dock.
love it

---

### Post by Frogs Hair on 2012-03-22
> **miatawnt2b said:**
> I just switched to cairo dock.
love it

Great ! I tried the Cairo dock stand alone session two weeks ago and it worked pretty well . I have been experimenting with Classic Gnome and have Dockbarx installed at the moment.

---

### Post by Adam_GUI on 2012-03-23
Throughout today, I added the medibuntu repo, ran system updates, and added a skype icon to my AWN dock.

Somewhere, between those three things, the green plus sign has vanished.

Still at version 4.0.1.

Looks like the key could be as simple as dragging any icon from the programs menu directly over the plus sign on the dock.  But, I can't confirm that as a definitive.

---

### Post by dv310p3r on 2012-04-01
> Looks like the key could be as simple as dragging any icon from the  programs menu directly over the plus sign on the dock.  But, I can't  confirm that as a definitive.     While two people doing the same thing and it working isn't definitive proof, it did work for me as well. Thanks a million.

---

### Post by Adam_GUI on 2012-04-02
> **dv310p3r said:**
> While two people doing the same thing and it working isn't definitive proof, it did work for me as well. Thanks a million.

It isn't a cure all.  :(
After another system reboot or killing and restarting awn, the plus sign comes back whenever it feels like it.

I'm staring at it right now as it sits to the right of my exaile launcher.

It still isn't malicious.  It's just there;  Taunting me as it knows I have no clue if there's a checkbox in some obscure menu to disable it.

---

### Post by lostmariner on 2012-10-14
I have the same problem. Dragging another program's icon over it makes it disappear, but still very wierd.

---

### Post by McLovin926 on 2012-11-16
> **Adam_GUI said:**
> Throughout today, I added the medibuntu repo, ran system updates, and added a skype icon to my AWN dock.

Somewhere, between those three things, the green plus sign has vanished.

Still at version 4.0.1.

Looks like the key could be as simple as dragging any icon from the programs menu directly over the plus sign on the dock.  But, I can't confirm that as a definitive.
I have actually tried this myself, once you add a launcher, (doesn't matter what it is), you can then delete said launcher, and the "plus" icon is gone, but when you restart AWN, it comes back, and you have to do it again, a bit of an inconvenience, but short dirty way around it for the moment.

---

### Post by ChrisOfBristol on 2012-11-22
Previous posters are correct in saying that it can be got rid of by right-clicking and either deleting it or editing it to insert the name of the program to launch, or by dropping an existing launcher over it. Unfortunately this only lasts until you logout, next time you login the horrible thing is back!

It is a bug which has been reported: [https://bugs.launchpad.net/awn/+bug/990774]("https://bugs.launchpad.net/awn/+bug/990774")
The fix mentioned in post 21 of that bug report works for me on Ubuntu 12.10 with gnome-session-fallback instead of Unity and post 22 mentions that it works on Linux Mint 13 64 Bit with MATE.

Open a terminal and type: **sudo apt-get libdesktop-agnostic-cfg-gconf**

---

### Post by Adam_GUI on 2012-11-22
Installing libdesktop-agnostic-cfg-gconf does remove the plus-sign/cross.
Note:
***You Will Have To Set Your AWN Preferences All Over Again!!!***

But, after some setup, it works.

[IMG]http://img.photobucket.com/albums/v481/kagerousama/AWN-Fix.png[/IMG]

---

### Post by makitso on 2012-11-23
[https://bugs.launchpad.net/awn/+bug/990774](https://bugs.launchpad.net/awn/+bug/990774)

apt-get build-dep avant-window-navigator
apt-get -b source avant-window-navigator
sudo dpkg -i avant*.deb


 That makes no sense.  How does simply recompiling fix the problem? ...  Well...
 On Debian, AWN stores its settings in '.gconf', but on Ubuntu, AWN stores its settings in *.ini files at ~/.config/desktop-agnostic/
 The difference in how AWN stores  its settings is probably set by flags (or whatever) during compilation  because the source and patch files downloaded by apt-get on both  machines are essentially identical.  There's probably a defect in the  code that loads the *.ini files.  Simply recompiling does not set  whatever special compile-time flags and creates a set of AWN packages  that stores settings in  '.gconf'.  Having '.gconf' around just for AWN  isn't 'elegant', but it's way better than that ugly plus icon.

---

### Post by redbob on 2013-03-15
This solution worked very well for me... As we tell here in Brazil: "Show de Bola!!" :-({|=

---

