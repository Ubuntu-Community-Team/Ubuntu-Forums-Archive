---
title: "Login problem  - half screen black - how to debug"
date: 2010-08-04
forum: Desktop Environments
---

### Post by pcolamar on 2010-08-04
Since a couple of days I am having a strange problem with my Ubuntu installation (Lynx 10.04)
After the startup phase, the right half of the screen turns black  (see pict) and the keyboard  starts responding very, very slowly.
So slow you cannot practically type your passwd in.
You can also notice a pixelated copy of the cursor into the black half.
I have tried without  success some solution proposed into this thread ([http://ubuntuforums.org/showthread.php?t=1542082]("http://ubuntuforums.org/showthread.php?t=1542082")) 

Can somebody help me debugging the problem ( or suggest a solution)

The PC is an Athlon 64 with ATI x300 on board, MESA driver is used for the videocard (ATI Catalyst compatible with Lucid  does not support the card anylonger !)

The problem seems really related to the user selection panel, indeed if I get in via one of the user that does not require passwd, I pass the login screen and everything works fine as long as I do not try to switch user.
Note that booting with Ubuntu 9.04 (I have a triple boot installation), all works fine .

---

### Post by kr651129 on 2010-08-04
Can you post your xorg.conf please?

---

### Post by pcolamar on 2010-08-05
Here you go: (Keep in mind that once logged in, all works fine)

---------- xorg.conf
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon X300 Pro "
        Monitor    "SyncMaster"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

---

### Post by pcolamar on 2010-08-05
bump

---

### Post by kr651129 on 2010-08-06
Did you install x86 or 64?

---

### Post by kr651129 on 2010-08-06
I may have found a solution for you, try installing the fglrx package

---

### Post by pcolamar on 2010-08-07
Ok, I found the problem.
My 3 years old boy had activated some zoom option of the "Universal Access Preferences" available in the lower left part of the GDM login screen that transforms the left part of the screen in a magnifier lens !
Oh boy ! I could have looked for ages for the root cause if he would not have done it again in front of me.

Thanks anyhow to all.

P.

---

### Post by pcolamar on 2010-08-07
kr651129, unfortunately, my old x300 card is not supported any longer by fglrx.

---

### Post by bjornjul on 2010-08-10
> **pcolamar said:**
> Ok, I found the problem.
My 3 years old boy had activated some zoom option of the "Universal Access Preferences" available in the lower left part of the GDM login screen that transforms the left part of the screen in a magnifier lens !
Oh boy ! I could have looked for ages for the root cause if he would not have done it again in front of me.

Thanks anyhow to all.

P.

Man alive ... same thing happened to me, except the boy is five ;-)

The icon in my case was in the low right corner ( Universal access prefrences ) 

Thanks for the help :-)

---

### Post by keithclark on 2010-11-12
> **pcolamar said:**
> Ok, I found the problem.
My 3 years old boy had activated some zoom option of the "Universal Access Preferences" available in the lower left part of the GDM login screen that transforms the left part of the screen in a magnifier lens !
Oh boy ! I could have looked for ages for the root cause if he would not have done it again in front of me.

Thanks anyhow to all.

P.

How do you get out of the magnifier?  I do not see the button on the lower right corner, as the magnifier only shows black and is sitting on top of the entire right hand side of my screen.

Keith

---

### Post by pcolamar on 2010-11-13
Keithclark,
  honestly speaking , I do not remember all the steps but......
I guess, I got in via one of the profiles that did not require passwd and then via sudo I reset the pwd of the administrator (I have webmin installed on the pc).
Got back in again as administrator and via synaptic deinstalled the unneeded pack.ges.
I am  sure you can also try to open a shell via ALT+CTRL+F2...F6 and do all in it. I am just not very experienced (any longer, sigh !) via shell command or ssh if your PC is on a lan.
I hope thishelps.

Cheers
Palmer

---

### Post by KyleCF on 2011-01-14
Sorry for posting on a closed thread, but the answers given do not solve it for me. I'm still relatively new at Ubuntu, and although I now realise that the problem I'm having is magnifier related, I have absolutely no idea how to solve it. I don't know what sudo code to use, and I don't even know if a GUI equivalent exists to solve the problem. Can someone please post a proper answer?

Many thanks

---

### Post by TaTaE on 2011-01-24
Try this solution:

boot in safe mode

enter this in your prompt:

```
sudo aptitude purge gnome-mag
```

good luck


[ My 3 years old did this to me, too. ]

---

### Post by stinkeye on 2011-01-24
> **KyleCF said:**
> Sorry for posting on a closed thread, but the answers given do not solve it for me. I'm still relatively new at Ubuntu, and although I now realise that the problem I'm having is magnifier related, I have absolutely no idea how to solve it. I don't know what sudo code to use, and I don't even know if a GUI equivalent exists to solve the problem. Can someone please post a proper answer?

Many thanks

```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```
Will turn the magnifier off at the gdm screen.

---

