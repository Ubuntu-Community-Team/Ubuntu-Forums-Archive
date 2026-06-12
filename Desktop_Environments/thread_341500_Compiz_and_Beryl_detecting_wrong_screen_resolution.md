---
title: "Compiz and Beryl detecting wrong screen resolution"
date: 2007-01-18
forum: Desktop Environments
---

### Post by elempoimen on 2007-01-18
I'm running Edgy on an HP Pavilion laptop, and have gandalf's builds of Compiz installed. My machine has an Intel i945 graphics adapter, and works perfectly using Xgl/Compiz on openSUSE. I'm impressed that Edgy has AIGLX compiled in with the drivers...and all seems to be good as far as regular OpenGL acceleration is concerned.

Initially, when I installed Edgy, my screen wouldn't run any higher than 1024x768. I was able to reconfigure Xorg to support the native resolution of my monitor, 1280x800. I have allocated 32 MB of RAM to the graphics, using Xorg. 915resolution does list the correct graphics mode as being available, so there is no need for me to patch it.

Here's my problem: when I start either Compiz or Beryl, they seem to still detect my desktop resolution as 1024x768. The right side of my desktop and panel is cut off, and while I can drag windows there, I end up with display corruption. Windows maximize to the 1024 width. Additionally, the window picker in the panel stops showing window titles. Other than this problem, Compiz and Beryl seem to work properly.

Not sure if it's related or not, but KXDocker (which also uses compositing) shows a black bar across the bottom of the desktop when it does a mouseover zoom.

How do I get Compiz to pick up on the correct resolution?
[URL="http://123pichosting.com/images/3187screenshot1.png"]
Here is a screenshot of the problem[/URL].

---

### Post by manutdfan2850 on 2007-01-19
wow i have the exact saame problem but I have a ATI mobilitry radeon 9100 igp

what can I do to fix this? 

plz see screenshot

---

### Post by elempoimen on 2007-01-19
So it's not a chipset issue. I suspected. I think it's an X server thing. Maybe something needs to be changed in xorg.conf? I saw a similar issue on ExtremeTech: [http://discuss.extremetech.com/forums/1004362409/ShowPost.aspx](http://discuss.extremetech.com/forums/1004362409/ShowPost.aspx). I find that the only way I can get my desktop back to normal after disabling Compiz is either to change resolutions or dink around with the panel positions.

---

### Post by manutdfan2850 on 2007-01-19
yay i got it to work on proper resolution! 

here are the sources i used to get it fixed:

[http://ubuntuforums.org/showthread.php?t=326173&highlight=beryl+resolution](http://ubuntuforums.org/showthread.php?t=326173&highlight=beryl+resolution)
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)
[http://ubuntuforums.org/showthread.php?p=2010643#post2010643](http://ubuntuforums.org/showthread.php?p=2010643#post2010643)

hope it helps

---

### Post by elempoimen on 2007-01-20
Nope. Didn't work for me, but thanks! Now my windows are centered...at 1024 width...but the panel still gets cut off. There must be something peculiar to the Intel chipset.

---

### Post by elempoimen on 2007-01-21
I got it!  Here's what I came up with: I had used Xorg to set my  video ram. I commented out that line, and everything worked fine. I did use the AGPSize setting,

---

