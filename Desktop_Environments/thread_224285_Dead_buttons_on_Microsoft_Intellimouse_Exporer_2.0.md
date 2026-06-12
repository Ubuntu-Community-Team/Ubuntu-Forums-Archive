---
title: "Dead buttons on Microsoft Intellimouse Exporer 2.0"
date: 2006-07-27
forum: Desktop Environments
---

### Post by trojanlinux on 2006-07-27
When I go to mouse settings it only shows me button configurations for simple two button mouse. How do I program the other buttons?

Thanks!

---

### Post by reclusivemonkey on 2006-07-27
As far as I know, there isn't a nice GUI for this; also I am not sure what you actually want to program your extra mouse buttons to do. I use mine mostly in XGL/Compiz. In /etc/X11/xorg.conf I have;

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

```

and then I can use Button6 and Button7 for the side buttons on my mouse. However if you want to do anything more complex, this may not help.

---

### Post by its_me_gb on 2006-07-27
Thanks for this, i've been trying for ages to get my side buttons to act properly, this is the first solution i have found that works!!

---

### Post by trojanlinux on 2006-07-27
I want to use the side buttons for forward and back on the web browser. How would i set this up?

---

### Post by trojanlinux on 2006-07-27
also when i try to save an entry it says you are not the owner. how i sign on as the owner? i am using the login i made with the install

---

### Post by RickShelton on 2006-07-28
Try sudo gedit /etc/X11/xorg.conf
That will allow you temp root access.
Enjoy!

---

### Post by trojanlinux on 2006-07-28
> **RickShelton said:**
> Try sudo gedit /etc/X11/xorg.conf
That will allow you temp root access.
Enjoy!

thanks! Now all i need is help getting the side buttons programed for forward and back, anyone have any ideas?

---

### Post by reclusivemonkey on 2006-07-28
> **trojanlinux said:**
> thanks! Now all i need is help getting the side buttons programed for forward and back, anyone have any ideas?

Hmm, not sure why they don't... mine do in Firefox and I've not done anything to make them! :-S

---

### Post by Anduu on 2006-07-28
> **reclusivemonkey said:**
> Hmm, not sure why they don't... mine do in Firefox and I've not done anything to make them! :-S

Yup...If you modify your xorg.conf as stated your side buttons should work for forward and back...

---

