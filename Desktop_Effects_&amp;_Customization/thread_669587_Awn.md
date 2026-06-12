---
title: "Awn"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by muntaser on 2008-01-16
Can someone help pls! Mine configuration does not work!
I got to the place where I press alt+F2, and fill that thing and select it and press "run". However after I did that no bar/dock appeared. So I did it again and selected "run in terminal" and then the message below appeared in the terminal:
"Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."
What shall I do next??

---

### Post by jamesey on 2008-01-16
I'm a noob, so someone else will need to fill in details, but basically you need to:

make sure your restricted drivers or upgraded drivers are installed. do that and restart.
> sudo apt-get install xserver-xgl
install compiz or If it's already installed (7.10) you need to enable composting in your xorg.conf (change something from 0 to a 1)
reboot

then run AWN.

---

### Post by muntaser on 2008-01-16
> **jamesey said:**
> I'm a noob, so someone else will need to fill in details, but basically you need to:

make sure your restricted drivers or upgraded drivers are installed. do that and restart.

install compiz or If it's already installed (7.10) you need to enable composting in your xorg.conf (change something from 0 to a 1)
reboot

then run AWN.

how can i enable compositing?

---

### Post by rune0077 on 2008-01-16
type this in a terminal: 

```
sudo gedit /etc/X11/xorg.conf
```

Find the location where it says:

Section Extensions

If it here says either

```
Option "Composite" "0"
```
or
```
Option "Composite" "Disabled"
```

then change it to:

```
Option "Composite" "Enabled"
```

Then save the file, hit ctrl+alt+backspace and log back in.

If this doesn't fix your problems, then it's probably to do with your drivers and/or your graphics card, but try that first.

---

### Post by glennric on 2008-01-16
Have you enabled compiz?  Go to
"System->Preferences->Appearance",
select the "Visual Effects" tab,
and select Normal (or Extra if you have a good enough video card).
If that doesn't work then try some of the other suggestions here.

---

