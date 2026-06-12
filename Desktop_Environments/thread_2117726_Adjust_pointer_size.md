---
title: "Adjust pointer size"
date: 2013-02-19
forum: Desktop Environments
---

### Post by pstrbrc on 2013-02-19
Ubuntu 12.04LTS
Have had it set up with Unity (very annoying!) and all the Gnome choices I can find. Have been through System Settings and Advanced System Settings, have searched the WWW, and I am stuck.
I'm not blind, just have an eye condition that leaves me with a varying level of astigmatism at any given time. As long as stuff is holding still, I see it fine, but moving things? Bah! So, the only moving thing in my desktop environment I need to be able to pick up on and follow is the da@@@ed pointer. I don't want larger font. I don't want more contrast. I just want a 3x larger pointer!

Please help an old guy!

Bruce

---

### Post by zombifier25 on 2013-02-19
Install dconf-tools first:
```
sudo apt-get install dconf-tools
```
Then launch dconf-editor from Unity or the command line, go to org -> gnome -> desktop -> interface, and change the value cursor-size to a larger value.

---

### Post by pstrbrc on 2013-02-19
That would seem to make sense to me, too. But I only get a larger cursor in LibreOffice applications and those that a text window opens in. Fer instance, I have one in this text window, but not the rest of the page. I have the small cursor on the desktop or when a file manager is open. 
When using any of my teaching programs (I teach secondary math, so everything from CaRMetal, graph monkey, and Qalculate to just plain old Adobe Reader 9) all I have is a little pointer. I have set the value for the cursor size up to 120, and in those apps that do change, I get a huge pointer. But not the desktop, not the programs I use for teaching. Other suggestions? 
(btw, I know to do a complete shutdown and reboot. Makes no difference.)

---

### Post by cmcanulty on 2013-02-19
on some machines dconf-tools will change the pointer size and color and on some even identical machines it does nothing. This is another instance of something that was easy to change in gnome 2 and a mess now.

---

### Post by stinkeye on 2013-02-19
See [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046") thread.
It depends on what release your using.
In 12.10 you need to make 2 settings changes.
In 12.04 you need to install a custom large cursor.

---

