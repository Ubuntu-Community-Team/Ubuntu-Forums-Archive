---
title: "Making screen resolution persist"
date: 2009-06-07
forum: General Help
---

### Post by Bruno De Barros on 2009-06-07
It's been well past a month since I got a new computer monitor my Ubuntu computer, and every time I boot up the computer, the resolution is at 1024x768, I have to manually go and change it to 1680x1050, and afterwards the items in my panels usually are in a different position as well, which really frustrates me. Is there any way to fix this issue? Thanks in advance.

---

### Post by ajgreeny on 2009-06-07
You should be able to change the resolution in System>Preferences>Display, and they should stick, or maybe if you have a proprietary graphics driver you need to change it in whichever proprietary driver configuration application is available.

---

### Post by Bruno De Barros on 2009-06-07
That's what I do every single time the computer boots up, but when I log out and log in again, or when I restart the computer, I have to do it again! :(

---

### Post by ajgreeny on 2009-06-07
You can try editing your /etc/X11/xorg.conf file with the res you want in the following format
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80   #get these figures from your display documentation if you need to, but it may not be needed
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1680x1050" "1280x1024" #add other useful resolutions here.
    EndSubSection
EndSection
```I hope this helps.  If not I don't know what else to suggest.

---

### Post by Bruno De Barros on 2009-06-09
What I did was add the Modes line to the xorg.conf file, but it didn't do anything. So then I opened the display settings, and it asked me if I wanted to use the graphic driver vendor's tool, and I said no (i had always said yes, before), and then I changed the screen resolution, and it stayed! I rebooted my computer, and it's still here! :D

---

### Post by slimsim on 2009-07-25
I was having the same problem, and even saved the xorg.conf file after using the command:

gksudo nvidia-settings

from the terminal.    This lets you run nvidia display manager as root, and thus save the xorg.conf file.

HOWEVER that did not help me, as the resolution would reset everytime I  logged out.  

What the above user said also corrected my problem; Select "no" when the popup asks if you want to use the vendor's display manager.

bump for anyone else who has had this problem.  There is a problem with nvidias display driver tool.

---

