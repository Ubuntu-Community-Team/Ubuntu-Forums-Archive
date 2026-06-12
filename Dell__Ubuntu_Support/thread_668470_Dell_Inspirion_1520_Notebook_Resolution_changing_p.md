---
title: "Dell Inspirion 1520 Notebook Resolution changing problems in Ubuntu 7.10"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by ciuci on 2008-01-15
after a little struggle i've managed to install the wireless adapter, sound card and video card (nvidia 8600 gt mobile) on my 1520 inspirion notebook... when i change the resolution of the screen to it's native one, everything goes according to plan ... i a get crisp, bright, not streched, and crystal clrear image.... so far so good... but when i reboot, the resolution goes back to the original one (1024*768) which kinda' sucks, because i have to change it again, and move all my icons on the two panels back to where they were! 
has anyone got a solution to this problem??

---

### Post by RebounD11 on 2008-01-15
Try editing your xorg.conf. In the Modes subsection add the resolution(s) you use or wish to use.

It should look sth like this:
```

Section "Screen"
    ...
    SubSection     "Display"
        Depth       24
        Modes      "1600x1280" "1600x1200" "1480x1024" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by ciuci on 2008-01-15
okay, i tryed that like 10 times, but every time i reboot, xorg.conf just gets back to where it was, as if some magical doohickey comes around my back and undos everything i've done!! :confused:



(ps. wow, ce coincidenta :D esti roman, si uitete si la semnaturi!!!!)

---

### Post by ciuci on 2008-01-16
HELOOOOOOO!!! ANY BODY THEREEEE???? does anyone know why my xorg.conf is so stubborn???

---

### Post by irish8890 on 2008-01-16
Download the proprietary nVidia drivers and the nVidia tools from the nVidia website.  This worked for my D630 with the NVS Quadro1 135.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

You have to shutdown graphics server and run the nVidia script in terminal mode.

Hope this helps.

John

---

### Post by ciuci on 2008-01-17
but i already have the nvidia proprietary drivers!

---

### Post by ciuci on 2008-01-17
any other ideas?

---

### Post by Mavtech on 2008-01-18
Are you changing the res in Ubuntu or on the Nvidia settings?  You should be doing it on the Nvidia settings if you are using the restricted driver.  I'm installing Ubuntu on my 1520 right now.  So, I'll let you know how it goes.

---

### Post by ciuci on 2008-01-19
well i  tryed both in "Screens and Graphics" in the Administration menu and in Nvidia settings, without any resut, but just 5 minutes ago i went into the "Preferences->Screen Resolution" box and clicked on "Make default for this computer" and the problem went away :D

---

### Post by Mavtech on 2008-01-19
Whenever I make a change with the Nvidia settings, it won't hold in the xorg because you don't have rights to write to it.  So, I do a preview of the xorg, copy it, and then open the xorg with "sudo gedit".  I then paste, save, and reboot to make sure the changes stayed.

---

