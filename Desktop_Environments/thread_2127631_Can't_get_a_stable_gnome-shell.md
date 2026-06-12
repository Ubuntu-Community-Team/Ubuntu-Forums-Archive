---
title: "Can't get a stable gnome-shell"
date: 2013-03-20
forum: Desktop Environments
---

### Post by bhosada on 2013-03-20
So I installed gnome-shell, all seems good until about a day in, all of a sudden everything becomes unresponsive, I can't click anywhere, I can't press SUPER to get to overlay, the only things I can do is watch the mouse move around, and watch my keyboard capslock light turn on and off as I hit the capslock button... this has happened atleast 3 times to me now. Using the great and almighty (yeah right) nvidia driver, I don't even have access to the virtual terminals, so I switch to those and seeing them fail hit the keys to get back to gnome-shell, now all I get is a black screen, with a moving cursor, nothing else. Only "solution" at this point is to hard reboot the system...

Only specifics I can remember is from the last incident, I was attempting to use the uploader on imageshack, next to "Activities" where gnome-shell shows the foremost program name, it changed to the image uploader title, and then just pretty much locked up. It always happens when I click something and need something to come to front.

Ubuntu: 12.10
Kernel: 3.5.0-17-generic
Arch: x86_64
Nvidia: 310.14

---

### Post by Frogs Hair on 2013-03-20
Make sure if you have installed any themes they are Gnome 3.6 compatible especially shell themes, but GTK as well.  Incompatible shell themes freeze sometimes and the overview, applications and notification   don't work properly. Other than that that it may be a hardware problem .

---

### Post by kurt18947 on 2013-03-20
I had problems with gnome-shell in 12.10 as well. My problems had to do with suspend/resume, specifically it wouldn't resume.  I installed Xfce which seemed better than gnome-shell.  Gnome-shell is working well in 13.04 for me to date.

---

### Post by bhosada on 2013-03-20
> **Frogs Hair said:**
> Make sure if you have installed any themes they are Gnome 3.6 compatible especially shell themes, but GTK as well.  Incompatible shell themes freeze sometimes and the overview, applications and notification   don't work properly. Other than that that it may be a hardware problem .

I haven't installed any themes, but have installed extensions, weather(neroth) and noa11y; possible culprits?
Doubt it could be hardware, as I also have Windows 7 and OS X installed on this box, and both are perfectly stable.

---

### Post by tancrackers on 2013-03-21
What graphics card(s) do you have? That could be a problem with Gnome Shell and graphics.

---

### Post by bhosada on 2013-03-21
nvidia 8800 GTX

---

### Post by Frogs Hair on 2013-03-21
> **bhosada said:**
> I haven't installed any themes, but have installed extensions, weather(neroth) and noa11y; possible culprits?
Doubt it could be hardware, as I also have Windows 7 and OS X installed on this box, and both are perfectly stable.

Try disabling the extensions as a test. I run an 8 series Nvidia card with the 304 experimental driver and have no problems on my W7 dual boot. 
Desktops include  Unity, Gnome Shell, and XFCE session.

---

