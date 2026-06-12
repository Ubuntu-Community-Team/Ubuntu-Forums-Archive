---
title: "keyboard and dial-up problems"
date: 2005-05-07
forum: Desktop Environments
---

### Post by GOwin on 2005-05-07
XFCE is my preferred window manager.

I have some problems though.

1) I use a notebook with a Japanese keyboard layout. Whenever I'm logged-in to Gnome, everything works out okay. However, if I log into xfce, it revert to a different layout. 

Running gnome-keyboard-properties doesn't seem to help. It says there that I'm on a 106-japanese keyboard but everytime I press  "]" key returns a "\" instead.

Kinda similar to this [http://ubuntuforums.org/showthread.php?t=28638](http://ubuntuforums.org/showthread.php?t=28638) except that I'm on XFCE.

2) I only have a dialup connection. To get my system to dialout I have to run network-admin and activate the modem connection. Fine with me. but everytime I have to dialout, I have to re-enter the dialup number everytime. Why can't the system remember my last input settings?

I also attempted to use gnome-ppp. It would dial-out but then it connects momentarily and then it disconnects again. I never get to connect to the internet using gnome-ppp

On a related note, is there any icon/applet for XFCE that would show whether I'm online or not? Right now, I have to check the modem lights or the network-admin.

That's all for now. I just got to say that this is the best distro I've tried so far. In fact, this is the longest I've stayed on. My laptop now boots to Ubuntu on DEFAULT.

Thanks.

---

### Post by jodef on 2005-05-07
[QUOTE=GOwin]XFCE is my preferred window manager.

I have some problems though.

1) I use a notebook with a Japanese keyboard layout. Whenever I'm logged-in to Gnome, everything works out okay. However, if I log into xfce, it revert to a different layout. 

Running gnome-keyboard-properties doesn't seem to help. It says there that I'm on a 106-japanese keyboard but everytime I press  "]" key returns a "\" instead.

Kinda similar to this [http://ubuntuforums.org/showthread.php?t=28638](http://ubuntuforums.org/showthread.php?t=28638) except that I'm on XFCE.

2) I only have a dialup connection. To get my system to dialout I have to run network-admin and activate the modem connection. Fine with me. but everytime I have to dialout, I have to re-enter the dialup number everytime. Why can't the system remember my last input settings?

I also attempted to use gnome-ppp. It would dial-out but then it connects momentarily and then it disconnects again. I never get to connect to the internet using gnome-ppp

On a related note, is there any icon/applet for XFCE that would show whether I'm online or not? Right now, I have to check the modem lights or the network-admin.

That's all for now. I just got to say that this is the best distro I've tried so far. In fact, this is the longest I've stayed on. My laptop now boots to Ubuntu on DEFAULT.

Thanks.[/QUOTE]


There are a number of tools you could try for instance : pppconfig or wvdial. Just type **sudo pppconfig ** or **sudo wvdial** and enter the details required. I 
haven't installed gnome-ppp but I'll see if I encounter the same problem.

---

### Post by GOwin on 2005-05-07
thanks. i've tried those before, with no successful results. :|

I'm still wondering about the keyboard problem. all the other keys seems to work right except for the closing bracket which returns a backward slash.

any idea anyone?

---

### Post by GOwin on 2005-05-12
I have not managed to resolve the keyboard issue.

Anyone? 

[QUOTE=GOwin]XFCE is my preferred window manager.

I have some problems though.

1) I use a notebook with a Japanese keyboard layout. Whenever I'm logged-in to Gnome, everything works out okay. However, if I log into xfce, it revert to a different layout. 

Running gnome-keyboard-properties doesn't seem to help. It says there that I'm on a 106-japanese keyboard but everytime I press  "]" key returns a "\" instead.

Kinda similar to this [http://ubuntuforums.org/showthread.php?t=28638](http://ubuntuforums.org/showthread.php?t=28638) except that I'm on XFCE.
[/QUOTE]

---

### Post by Sepero on 2005-05-15
For changing your keys, do some research on xmodmap and xev.

---

### Post by GOwin on 2005-05-17
Thanks.

I managed to fix it by editing /etc/X11/xorg.conf to

Section "Keyboard"
     XkbRules "xorg"
     XkbModel "jp106"
     XkbLayout "jp"
EndSection

---

