---
title: "Setting specific HorizSync and VertRefresh for specific Resolution"
date: 2009-06-25
forum: General Help
---

### Post by port67 on 2009-06-25
Somewhere between my LCD monitor(MAG Innovision LT716s) and the X server the EDID is not being receive. I have bypassed this in my xorg.conf and have manually set the HorzSync and VertRefresh to the manufacture specs 

HorizSync   31.0-81.0
VertRefresh 60.0-75.0

I than via sudo nvidia-settings I set the screen resolution to 1280x1024 and apply. No problems everything works. I than save and exit nvidia-settings. The problem is when I restart the computer next time the login screen is set to the correct resolution but when I login the screen goes blank and and the LCD OSD says the input is not supported and the VertRefresh is 59.9 which is outside of the parameters I set in xorg.conf. :confused:

Is there a way to specify a specific HorizSync and VertRefrsh for a resolution. An example would be 1280x1024 with HorizSync 63.98 kHz and VertRefresh 60 Hz

Im not new to Ubuntu but I am new to having problems I cant find answers to in the forums

---

### Post by CatKiller on 2009-06-25
If you've already got the correct settings in xorg.conf, you don't need to run nvidia-settings as root to set the resolution.

Per-user resolution settings are stored in ~/.config/monitors.xml. Switch to a virtual console (Ctrl-Alt-F1) and rename this file to something else. Then switch back to the graphical environment (Alt-F7) and log in. You should get a new file with the default resolution set.

---

### Post by starcannon on 2009-06-25
Perhaps the XFree86 Modeline Generator could help?
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

GLAHF

---

### Post by port67 on 2009-06-25
Thanks for the suggestions, however the screen resolution is still at 1280x1050 after login. The problem I am having is that the vertrefresh is at 59.9Hz according to the OSD, and the screen cannot display anything below 60Hz. I don't get why it is at a lower frequency than what I have specified in the xorg.conf. I know it can get the correct horzsync and vertrefresh at 1280x1050 but only if I change it from a lower setting after I log in. All the frequencies that I am using are manufacture specified for each resolution.

---

### Post by randiroo76073 on 2009-06-25
You might try setting your xorg.conf to 62-65Hz and see if that helps. You can fudge a little between high & low.

---

### Post by port67 on 2009-06-26
I just tried changing the frequency, to no avail. the problem is that there are only two frequencies that the monitor works at when resolution is 1280x1024 Option 1 VR:60Hz & HF:63.98kHz or Option 2 VR:75Hz & HF:79.98kHz. By changing the bottom range of the VR to above 60Hz it switches to Option 2 and sets the HF to 81.2, again out of range of the monitor. :confused: I have also tried lowering the upper range of the HF, when x restarts the next time though it defaults back to 800x600 because it can't set the frequency for 1280x1024.](*,)

---

### Post by CatKiller on 2009-06-26
What does your X log say?

less /var/log/Xorg.0.log

I needed to put ```
        Option          "UseEDID"                       "False"
``` in the Device section of my xorg.conf because my monitor reports inaccurate numbers for screen size and DPI.

---

