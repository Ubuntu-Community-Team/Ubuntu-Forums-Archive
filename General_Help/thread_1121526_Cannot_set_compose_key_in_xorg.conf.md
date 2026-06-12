---
title: "Cannot set compose key in xorg.conf"
date: 2009-04-10
forum: General Help
---

### Post by maplon on 2009-04-10
I am running Xubuntu Intrepid 64bit (fresh install) on a Lenovo X61. I want to use the caps lock key as the compose key.

To do so, I added the following section at the end of my xorg.conf:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules" "xorg"
        Option          "XkbModel" "pc105"
        Option          "XkbLayout"  "us"
        Option          "XkbOptions" "compose:caps"
EndSection

```
But when I then do Ctrl-Alt-Backspace, X says it cannot parse the configuration file, and starts in low resolution mode (which I think uses etc/X11/xorg.conf.failsafe).

What is wrong with the section above, or is there any other way to set the compose key to CapsLock in Xubuntu/ Xfce?

Just to be complete, the rest of the xorg.conf is what is automatically generated, and looks like this (without the commented section at the beginning of the file):

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by VCoolio on 2009-04-10
Try the gui-way this time. For Ubuntu Intrepid this would be: Preferences > Keyboard > Layouts > Other options > Compose key position, tick the Capslock option. After you changed that and if it works, check the .conf file again to see what you did wrong.

---

### Post by Thura on 2009-04-10
I don't know much about xfce, but in gnome I cannot edit xorg.conf directly for keyboard settings, since kbd is overwriting them ...

xfce4-xkb-plugin  ?
[http://blog.kivisoo.eu/2009/03/xfce-and-keyboard/](http://blog.kivisoo.eu/2009/03/xfce-and-keyboard/) 

But to be honest, I have never used xfce personally ...

---

### Post by maplon on 2009-04-10
> **VCoolio said:**
> Try the gui-way this time. For Ubuntu Intrepid this would be: Preferences > Keyboard > Layouts > Other options > Compose key position, tick the Capslock option. After you changed that and if it works, check the .conf file again to see what you did wrong.

Thanks, but to my knowledge, no GUI option exists on Xfce.

---

### Post by maplon on 2009-04-10
thanks.

> **Thura said:**
> I don't know much about xfce, but in gnome I cannot edit xorg.conf directly for keyboard settings, since kbd is overwriting them ...


But that's not even my problem. My problem is X hiccuping on the section in the xorg.conf. 

> **Thura said:**
> 
xfce4-xkb-plugin  ?


I am using this and it doesn't do anything about the compose key.


> **Thura said:**
> 
[http://blog.kivisoo.eu/2009/03/xfce-and-keyboard/](http://blog.kivisoo.eu/2009/03/xfce-and-keyboard/) 


I'm not sure I understand this either. The xorg.conf section looks identical to the one I have in all the relevant bits, but for me, X doesn't like this.

---

### Post by maplon on 2009-04-15
I managed to solve this by adding the line about "CoreKeyboard" (see below), and I moved the section to the beginning of the xorg.conf file. I don't know what did it, but now it works.

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules" "xorg"
        Option          "XkbModel" "pc105"
        Option          "XkbLayout"  "us"
        Option          "XkbOptions" "compose:caps"
EndSection 

```

---

### Post by jonkulp on 2009-05-09
This solution didn't work for me--very annoying since I've always been able to add the keyboard option to xorg.conf successfully in the past--but I found another way to do it.  This command will set the compose key to the right alt key:

```
setxkbmap -option compose:ralt
```

To have this set automatically, add the command to your startup applications by going to "Applications>Settings>Session and Startup" and clicking on the "Application Autostart" tab.  Click "Add" and give it a name, then put the aforementioned command in the command field.  Now when you log in, the compose key will be set.

---

### Post by susokukan47 on 2009-07-04
hey, thanks jonkulp! i'm a relative novice with ubuntu and i didn't want to mess around with xorg.conf. now i can type macrons for my latin studies all day :-)

---

### Post by foresto on 2009-10-22
I don't think XFCE offers a GUI for this, but you can edit /etc/default/console-setup to contain this line:
XKBOPTIONS="compose:caps"
(and then restart X)

To discover which keys you can use other than Caps Lock, run:
grep compose: /usr/share/X11/xkb/rules/xorg.lst

More info:
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

