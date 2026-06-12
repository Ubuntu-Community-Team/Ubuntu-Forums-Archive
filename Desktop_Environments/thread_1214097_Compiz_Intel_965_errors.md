---
title: "Compiz Intel 965 errors"
date: 2009-07-15
forum: Desktop Environments
---

### Post by Ratscallion on 2009-07-15
Hello! I've been using Jaunty for sometime, and now the lack of compiz is starting to bug me (pun). 

I've got an Intel 965 graphics card and am well aware it is currently blacklisted in Compiz. I've used all of the workarounds mentioned on the compiz Wiki, mainly the 
```
SKIP_CHECKS=yes compiz(-manager)
```When I try this, nothing compizy happens, I just get an output and the Terminal just ends the process. The output is as follows:
> :~$ SKIP_CHECKS=yes compiz

sam@ubuntu:~$ Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Any ideas for compiz? Thanks.

---

### Post by Mia1990 on 2009-07-15
try running compiz from the terminal and see if it gives a error

---

### Post by Ratscallion on 2009-07-15
Same error as above...

---

### Post by Mia1990 on 2009-07-15
i am guessing you have the ccsm installed look under hardware drivers and see if you have a driver installed.

---

### Post by Ratscallion on 2009-07-15
Yeah, I have the ccsm. Under Hardware Drivers I only have the madwifi driver for my wifi card, which is not activated.

---

### Post by Mia1990 on 2009-07-15
ok do this
sudo gedit /usr/bin/compiz

look down were it says blacklist based on the pci ids and see if your card is listed there
or just post it on here i'm sure it is as i just looked on wiki and it was you can check it out @wiki.compiz-fusion.org/Hardware/Blacklist for details

---

### Post by Ratscallion on 2009-07-15
> # blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

That help?

---

### Post by Mia1990 on 2009-07-15
you un blacklisted you card already?It should be working then

---

### Post by Mia1990 on 2009-07-15
no never mind this is your card here
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
that's the one you should unblacklist

---

### Post by schmolch on 2009-07-15
Not sure why you mess around with the blacklisting when you use skip-check from the beginning.

However, if your current WM (probably metacity) is displaying shadows, then you have to disable its compositing manager.
Do that in gconf-editor, restart it, and try again, that worked for me.

---

### Post by Ratscallion on 2009-07-16
Thanks for all your replies. I'll try what I think I got from that:
Unblacklist the card 
Make compiz the compositor
Try that
Otherwise,
Keep the card blacklisted
Make compiz the compositor.

I'll try both of the above and get back to you on both instances. Thanks for all your help!

---

