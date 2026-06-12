---
title: "how to disable (3d hardware acceleration) in 9.04 gnome.?"
date: 2009-06-05
forum: General Help
---

### Post by agel1 on 2009-06-05
can somebody tell me how to disable (3d hardware acceleration) in 9.04 gnome.?

thanks

---

### Post by aptgetmoo on 2009-06-05
Like disabling the driver?

---

### Post by Ocxic on 2009-06-05
3D acceleration is set by your hardware drivers/video drivers, to my knowledge you cannot disable it, unless your hardware/drivers have option for this.

if your talking about the 3D/compiz effects you can disable them from the appearance preferences.

---

### Post by agel1 on 2009-06-05
> **Ocxic said:**
> 3D acceleration is set by your hardware drivers/video drivers, to my knowledge you cannot disable it, unless your hardware/drivers have option for this.

if your talking about the 3D/compiz effects you can disable them from the appearance preferences.thank you, i know what compiz is, i need to turn off 3d hardware acceleration. 

in mandriva 2009.1 installed in the same computer i can disable it

---

### Post by Agent ME on 2009-06-05
Do you want to make compiz stop using acceleration, make compiz look simpler, or stint your computer by disabling acceleration completely by removing the driver? Doing the last thing is most likely not what you want to do and will likely slow down your computer considerably.

---

### Post by aptgetmoo on 2009-06-05
Agent ME is right. You can switch to VESA driver but your Ubuntu will become slow, for example when you scroll in firefox.

Anyway, any particular reason you want to disable 3d?

---

### Post by agel1 on 2009-06-05
> **aptgetmoo said:**
> Agent ME is right. You can switch to VESA driver but your Ubuntu will become slow, for example when you scroll in firefox.

Anyway, any particular reason you want to disable 3d?i want to disable it because when i switch user the screen goes black and i have to press the power buttom in the computer, i know the problem is the (3d hardware acceleration) because in mandriva was solved turning it off

i havent noticed any performance difference in mandriva, my card is i845g (sucks)

---

### Post by aptgetmoo on 2009-06-05
I think maybe you should paste your xorg.conf here first. its located in /etc/xorg/xorg.conf
or if you just want to edit the file here it goes:

First backup your xorg file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then edit the xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

Look under the "Device" section, and add the line below:
```
Driver         "vesa"
```

So it should be something like:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver         "vesa"
EndSection
```

---

### Post by Yellow Pasque on 2009-06-05
Rather than running the VESA driver, it would probably be better to install libgl1-mesa-swx11

---

### Post by agel1 on 2009-06-06
i disable it using driconf

now i can log out and switch user without problems

gracias a todos

---

### Post by aptgetmoo on 2009-06-06
Can you explain how did you do that?

---

### Post by colau on 2009-06-06
> **agel1 said:**
> i disable it using driconf

now i can log out and switch user without problems

gracias a todos
Does disabling 3d effect have effect on running windows xp?

---

### Post by aptgetmoo on 2009-06-06
> **colau said:**
> Does disabling 3d effect have effect on running windows xp?

No, this only disables 3d-acceleration on Ubuntu. Windows XP is independent of Ubuntu.

---

### Post by colau on 2009-06-06
> **aptgetmoo said:**
> No, this only disables 3d-acceleration on Ubuntu. Windows XP is independent of Ubuntu.
Thanks for your quick reply.;)

---

### Post by ppcuser on 2009-06-07
> **agel1 said:**
> i disable it using driconf

now i can log out and switch user without problems

gracias a todos
I wud also like to know how to do this - disable hardware graphics acceleration.
Have old GEforce 6000 series card, possibly damaged, that hangs/freezes when acceleration is used with GUI.
Any hints?

---

### Post by Yellow Pasque on 2009-06-07
There's a package called driconf. Install it. You can then find it under the System >> Preferences menu.

---

### Post by agel1 on 2009-06-07
There's a package called driconf. Install it. You can then find it under the System >> Preferences menu.

yeah is like this

---

