---
title: "gnome network manager gone"
date: 2010-05-30
forum: Desktop Environments
---

### Post by xpluto on 2010-05-30
hi 
 im using  lucid lynx, 10.04
i installed wicd  and then unistalled it
and i used pppoecof  to creat a connection and it worked well but now i can't find gnome network manager in the panel  it seem that it's gone! :(

  without it i can't creat vpn or see wirless networks

---

### Post by wojox on 2010-05-30
Try right click and Add to Panel 

Notification Area

---

### Post by xpluto on 2010-05-30
i tried  it add's an empty line to panel

---

### Post by xpluto on 2010-05-30
any help here? :(

---

### Post by SnickerSnack on 2010-05-30
Have you tried (1) running "killall gnome-panel" to restart the panel, (2) ending and restarting your gnome session, and (3) rebooting your computer?

---

### Post by xpluto on 2010-05-31
i entered these commands 
killall gnome-panel
and then sudo reboot  
it didn't fix it

---

### Post by ima5k on 2010-05-31
I think when you install wicd, the NetworkManager gets uninstalled.
Try to install it again.

*Btw, i thnik wicd is better

---

### Post by xpluto on 2010-05-31
i removed and installed but didn't work!

---

### Post by xpluto on 2010-06-01
**i think it is  a bug in gnome  i click in free space in panel in notification area and i can see the connection's !???!** :confused:
[[IMG]http://freeebayimagehost.com/images/q5zganxk1o6hgoeoe7ig_thumb.jpg[/IMG]]("http://freeebayimagehost.com/viewer.php?file=q5zganxk1o6hgoeoe7ig.jpg")

---

### Post by xpluto on 2010-06-01
i think the problem is here 
i used this code to reinstall panel this error appeared 
sudo apt-get purge gnome-panel;sudo apt-get install gnome-panel

---

### Post by xpluto on 2010-06-03
this problem is getting worse plzzzzz help :(

---

### Post by xpluto on 2010-06-06
Fixed removing everything from /etc/network/interfaces and replacing it  with:
 
 	Code:
 	 
auto lo
iface lo inet loopback 
:popcorn:

---

