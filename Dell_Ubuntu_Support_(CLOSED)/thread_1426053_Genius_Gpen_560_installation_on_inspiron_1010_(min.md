---
title: "Genius Gpen 560 installation on inspiron 1010 (mini 10), using karmic"
date: 2010-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by _thetrend on 2010-03-09
As a GMA500 user, I naturally have the karmic screen resolution fix. this has changed my xorg.conf file. Now I want to install a Genius Gpen 560 and I've gotten to the part where it's asking me to change my xorg.conf file, right after this line: 
```
sudo vim /etc/X11/xorg.conf
```

It says I have to insert something in the ServerLayout section, but this is my xorg.conf:

```

Section "Device"
        Identifier      "GMA500"
        Driver          "psb"
        Option          "IgnoreACPI" "true"
        Option          "MigrationHeuristic" "greedy"
        #Option         "DownScale" "false"
        #Option         "ExaNoComposite" "false"
        #Option         "ExaMem" "131072"
        #Option         "ExaScratch" "4"
        #Option         "ExaCached" "false"
        #Option         "LidTimer" "false"
        #Option         "NoAccel" "false"
        #Option         "NoFitting" "false"
        #Option         "NoPanel" "false"
        #Option         "ShadowFB" "false"
        #Option         "SWcursor" "false"
        #Option         "Vsync" "false"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        #Option         "Composite" "Enable"
        #Option         "RENDER" "Enable"
EndSection

```

any help would be so greatly appreciated! <3 I'm not very knowledgeable about tech stuff but I'd really like to be able to use my tablet ^^ (ps, I'm sorry if I put this in the wrong forum!)

---

