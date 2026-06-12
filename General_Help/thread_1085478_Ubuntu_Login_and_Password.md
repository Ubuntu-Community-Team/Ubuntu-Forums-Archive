---
title: "Ubuntu Login and Password"
date: 2009-03-03
forum: General Help
---

### Post by mpy on 2009-03-03
I typed in mike for my login and mike for my password.

I then get to this.

[http://i61.photobucket.com/albums/h49/Porta1992/ubuntupic.jpg](http://i61.photobucket.com/albums/h49/Porta1992/ubuntupic.jpg)

Now what? All I want to do is just get to my damn desktop.

---

### Post by geirha on 2009-03-03
Hm. It didn't send you directly to a graphical login screen? Did you install Ubuntu yourself? Do you see a graphical login screen if you hit Ctrl+Alt+F7 or Ctrl+Alt+F8 or Ctrl+Alt+F9?

---

### Post by mpy on 2009-03-03
> **geirha said:**
> Hm. It didn't send you directly to a graphical login screen? Did you install Ubuntu yourself? Do you see a graphical login screen if you hit Ctrl+Alt+F7 or Ctrl+Alt+F8 or Ctrl+Alt+F9?

I installed, little box comes up asks for a login and pw.

I set them both to mike.

I logged in to the thing, played a few games with I did some updates.

I finished updates and restarted the computer. It starts up goes through the loading bar then comes to this 'command prompt' asks for my ubuntu login. I typed in mike. then it asks for password. I typed in mike and then that log thing came it.

It is almost as if I am logged into my computer as text with no video.

Yes I installed it myself. I even reformatted the drive and reinstalled because of this problem. It happens after I update.

---

### Post by mpy on 2009-03-03
I just tried this.

mike
mike
startx

[http://i61.photobucket.com/albums/h49/Porta1992/ubuntu2.jpg](http://i61.photobucket.com/albums/h49/Porta1992/ubuntu2.jpg)

Thats what I got.

---

### Post by geirha on 2009-03-03
Sounds like the update installs a newer video driver that doesn't work with your video card then. Try booting the previous kernel. You do that by rebooting, and right after the BIOS, you should either see the GRUB menu, or a line like «Press 'ESC' to see the menu...». Press ESC to get to the menu, then choose the previous kernel (should be the third item on the list).

If that gets you to your desktop, open a terminal and run ```
sudo lshw -class display
``` and post that output here.

---

### Post by mpy on 2009-03-03
> **geirha said:**
> Sounds like the update installs a newer video driver that doesn't work with your video card then. Try booting the previous kernel. You do that by rebooting, and right after the BIOS, you should either see the GRUB menu, or a line like «Press 'ESC' to see the menu...». Press ESC to get to the menu, then choose the previous kernel (should be the third item on the list).

If that gets you to your desktop, open a terminal and run ```
sudo lshw -class display
``` and post that output here.


Okay I went to the third one.

Same stuff.

I just typed in the sudo lshw thing. This is what I got.

[http://i61.photobucket.com/albums/h49/Porta1992/lalala.jpg](http://i61.photobucket.com/albums/h49/Porta1992/lalala.jpg)


Its the right video card.

I just want to go to my desktop.

It starts up with the loading screen and then reverts back to this shitty text screen.


That is the GNOME Display Manager by the way.

---

### Post by mpy on 2009-03-03
Anything?

---

### Post by mulligan.can on 2009-03-03
Ok, sounds like your xorg.conf file is messed up. Did you manually install the nvidia drivers or use the repo version?

---

