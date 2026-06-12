---
title: "Problem with mouse and keyboard"
date: 2005-06-05
forum: Desktop Environments
---

### Post by leiterboss on 2005-06-05
The problem is that the keyboard just skips some keys I press, and the mouse pointer stops for about half a second in a given interval of time. It gets quite annoying after a while, and it doesn't happen with other linux distributions I have installed. Also, the problem occurs on both Gnome and KDE, but it doesn't in the login screen. 

The bizarre thing is that it doesn't happen all the time. In some logins it works all right and then, if I reboot, it does not. Can anyone help me with whatever the problem is?  :-P Thank you all in advance.   :) 

PS: More info I suppose it can be relevant: my PC is a laptop (so it's not a mouse, but a touchpad), and the installation is brand new.

---

### Post by intangible on 2005-06-17
When it's happening, try running System Monitor (gnome-system-monitor) reduce the update time to 1 sec (under Edit->Preferences) and see if any process is using a lot of CPU, sounds like something is stuck in a loop in the background using all your cpu.

---

### Post by naranjamecanica1 on 2005-08-23
I have the same problem, and is not the first time that happened to me, I did 3 o 4 Ubuntu Hoary install, and all the time been having the same problem, and as you say, its just happend sometimes.  ](*,) 
If theres someone that knows how to resolve this problem, I will really apreciated. Is the only problem that bothers me on Ubuntu.
I have a Compaq Presario, not a laptop like the other guy.
Also I used Fedora, Warty, SuSe, and I have no problems on them.


Please heeelllppppp!!!!

PD: Sorry for my poor english.

---

### Post by jcma on 2005-09-23
try to turn off powernowd.

it worked for me.

```
sudo /etc/init.d/powernowd stop
```

---

### Post by friendly_man on 2006-02-22
Hi,

I am having the same problem,  everytime I type the cursor skips backwards and starts over type over what I have already typed.

Unfortunately, I haven't been able to try powernowd, as I dont know where I can find this?  Please would someone be able to help.

Once again, thanks for your time.

---

