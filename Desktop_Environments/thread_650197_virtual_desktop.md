---
title: "virtual desktop"
date: 2007-12-26
forum: Desktop Environments
---

### Post by pavel989 on 2007-12-26
First of, lemme say that i figured that this was the right forum to post this is, because it is relating to desktops. With that being said:
What is a virtual Desktop you might ask?

well let's say that you current screen resolution is the ever so common 1024 by 768. what if you can have a much wider screen? Fonts and pictures stay the same, but you can scroll about your screen. It can have so much more room!

some setbacks:
Top and Bottom panels follow with it; your trash can and power down button are way right.
Might take a lot of memory (correct me on this)
If u maximize a window, the scroll is way right. (middle button on the mouse is nice here)
uhm also, if you have pidgin or another aim client, for example, if your messages on the bottom panel is                
[INDENT]on the far left, you wont really notice instant messages just by the flashing color if u pan to the far   right and it isn't in view .(just learn to move you applications around)
[/INDENT]

From what I understand, this cannot harm your computer


so heres how its done on an Ubuntu gutsy running xorg.

In a terminal type:
```
 sudo nano /etc/X11/xorg.conf
```

next scroll down to where it says:
```
Section "Screen"
        Identifier      "identifier"
        Device        "Device"
        Monitor        "Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050" "1024x768" (these are  mine, everything can be different)
        EndSubSection
EndSection
```

now under Modes put in:
```
Virtual number  number 
```
previously, 1024 is the would be the width of your screen, 768 is the height.
so here you can make it for example 1500 by 768 and scroll side ways or change the 768 and scroll up and down.

so now it should look something like this: (which is my setup)

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G400/G450"
        Monitor         "AL2223W"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050" "1024x768"
                Virtual 2200 1050
        EndSubSection
EndSection
```

hit ctrl+x, hit Y
save everything your doing
hit ctrl+alit+backspace
log back in, and go through system-preferences-resolution on your top panel.
scroll down and you new virtual should be there, if not, guess look for it.
and there ya have it. you can change it back and forth all you want. 


OTHERWISE:
There should be programs out there that can do this for you, maybe beryl, but i haven't tried yet.


PLZ send me corrections and or tips. I haven't heard of problems with this, but feel free to post.

---

### Post by TidusBlade on 2007-12-26
Sounds really good :) I thought something like that would be hard or break often, and I havent seen it in either Beryl or Compiz Fusion so Ill try it out soon and post back results.

---

