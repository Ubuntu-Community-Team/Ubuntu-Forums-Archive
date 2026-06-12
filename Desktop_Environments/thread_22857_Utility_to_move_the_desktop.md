---
title: "Utility to move the desktop?"
date: 2005-03-30
forum: Desktop Environments
---

### Post by konstantinos on 2005-03-30
My desktop is moved a bit off screen to the right.

I cannot set it to the correct position using the monitor's buttons, because then my Windows XP desktop gets off-screen.

Is there a utility that allows me to do this kind of tinkering?

I seem to remember Mandrake had something like this.

[Just to note: in both OSes I'm running the same resolution and refresh rate.]

Thanks for your help in advance.

---

### Post by erkki70 on 2005-03-30
Hi,
You could try to run Xvidtune to move your desktop and fit your screen.
To do so, open a terminal and type:
 ```
sudo xvidtune
``` 
Type in your password and you'll get a window where you can change the values.
I guess that in your case you should use the left or right button under HTotal:
This tool allows you to test before saving presets and also have the modline settings sent to the terminal, so last resort would be to tweak your Xorg config file (Hoary) or XF86Config (Warty) to achieve that.
Backup your .conf files in any ways.
Be cautious. ;)

Hope this helps.

---

### Post by carlc on 2005-03-30
I have an nvidia graphics card and was it the same position that you are. I followed the instructions for [installing nvidia drivers](http://ubuntuguide.org/#installnvidiadriver) and have not had any problems since.

---

### Post by Whiffle on 2005-03-30
You may want to make sure that you have the same refresh rate and resolution in both Windows and Linux, which should keep your desktop at about the same place.

---

### Post by konstantinos on 2005-03-31
[QUOTE=erkki70]You could try to run Xvidtune to move your desktop and fit your screen.
To do so, open a terminal and type:
 ```
sudo xvidtune
``` 
Type in your password and you'll get a window where you can change the values.[/QUOTE]
Erkki70, awesome! xvidtune was dead easy to work with, thanks again for the tip - problem solved.

[QUOTE=carlc]I have an nvidia graphics card and was it the same position that you are. I followed the instructions for installing nvidia drivers and have not had any problems since.[/QUOTE]
Carl, thanks for the tip - I've already solved my problem with xvidtune, but I'll keep you advice in mind.

[QUOTE=Whiffle]You may want to make sure that you have the same refresh rate and resolution in both Windows and Linux, which should keep your desktop at about the same place.[/QUOTE]
Whiffle, as I wrote in my first post:

[QUOTE=konstantinos][Just to note: in both OSes I'm running the same resolution and refresh rate.][/QUOTE]
But thanks anyway for your intention to help.

---

### Post by erkki70 on 2005-03-31
Hi konstantinos!
Great to know it did the trick for you.:lol:
Enjoy Ubuntu!

Cheers,

Erkki

---

### Post by Whiffle on 2005-03-31
[QUOTE=konstantinos]

Whiffle, as I wrote in my first post:

[/QUOTE]


Well I have been known to be blind before :D  :lol:

---

