---
title: "Mouse problem....Very simple...."
date: 2006-06-11
forum: Desktop Environments
---

### Post by Theprophet on 2006-06-11
OK just reinstalled Ubuntu and started from scratch... I have the Microsoft Intellimouse and well, The side buttons did not work. So, I edited the etc/X11/Xorg.conf file and then restarted X Tried the mouse and the scroll was working as the backward forward buttons and the side buttons were working as the scroll buttons. (The Opposite of what I need) I ran this command: 

xmodmap -e "pointer = 1 2 3 6 7 4 5"

Then, POOF! Works fine! So then I reboot and then the same problem comes back! I run the command and then its fixed again. The only problem is I have to do that EVERYTIME I reboot!!! How do I make it permanent??

Thanks in advanced,

The Prophet

P.S. I am a Linux Newb.

---

### Post by glotz on 2006-06-11
Put this to your /etc/X11/xorg.conf, in your mouse section
 Option          "ButtonMapping"         "1 2 3 6 7 4 5"
Or some variation of it.

---

### Post by ctgray on 2006-06-11
Or you could add that command to your Sessions Startup Programs maybe?

---

### Post by Theprophet on 2006-06-11
I added that line to the xorg.conf file but, it did not work. :-( 

What do you think I should do ? How would I go about adding it to my Sessions Startup Program??


-The Prophet

---

### Post by Theprophet on 2006-06-12
Nobdoy knows how I can fix this problem so I dont have to keep running this command on every start up? Please Help... 

-The Prophet

---

### Post by Ramses de Norre on 2006-06-12
To add it to your startup programs do system > preferences > session and then pick startup and fill in the command there, don't give it an order lower then 50.
(I hope the menu entries are correct, I don't use gnome anymore so look around for session if it's not there)

---

### Post by arizonagroovejet on 2006-06-12
[QUOTE=Theprophet]I added that line to the xorg.conf file but, it did not work. :-( [/QUOTE]

Did you reboot or restart the Xserver? Changes made to xorg.conf do not take effect until the Xserver is restarted.
I have a Logitech Mouseman Dual Optical which has a thumb button on it and I use the xorg.conf entry method to make the thumb button work.

You could also create a file in your home directory called .xmodmaprc and put in that the line

"pointer = 1 2 3 6 7 4 5"

Then log out an in again.
That will only enable the extra buttons for your user though. The xorg.conf method has the advantage that it will work for any user on the machine. I used  this method before it became possible to add info in xorg.conf

---

### Post by Theprophet on 2006-06-12
Damn...I tried EVERYTHING..I guess this just isnt going to work. Thanks guys for all your help. Ill just have to put in the command everytime I boot.


-The Prophet

---

### Post by glotz on 2006-06-12
[QUOTE=Ramses de Norre]To add it to your startup programs do system > preferences > session and then pick startup and fill in the command there.[/QUOTE]
.

---

### Post by Theprophet on 2006-06-13
Ok did that but still didnt work. I have a feeling I am forgetting something?? Anyways, I already had it in the start up commands, but the order was at 50 I changed it to 34, restart but, still didnt work. I have no idea why this is an issue last time I had Ubunut running on my lappy everything was working perfectly....

---

### Post by ubnoobie on 2006-06-13
i have a "5 button" (7 with wheel up/down) microsoft intellimouse 1.1a usb/ps2. offwhite w/ silver buttons, connected via the bundled usb -> ps/2 adapter.

i did not use xmodmap in dapper to get the side buttons working in firefox, which was the primary use for them. a quick edit to xorg.conf is all i did: 

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection
```

after a sudo dpkg-reconfigure xserver-xorg (mainly to specify display resolutions, but i also disabled 3 button emulation and chose the ExplorerPS/2 protocol), the only changes that were necessary was the addition of the last two lines in the section.

if i could find a non-convoluted way to get them working in other apps, i might try that later.. but all i was really concerned about was back/forward in firefox.

---

### Post by Theprophet on 2006-06-14
WOOOOOOO!!! It works I guess I just needed that extra command in the Xorg.conf file. AWESOME!! Thanks alot guys! Awesome support. That's why I love this distro.

\\:D/

---

