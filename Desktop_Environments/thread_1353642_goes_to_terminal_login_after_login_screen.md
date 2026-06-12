---
title: "goes to terminal login after login screen"
date: 2009-12-13
forum: Desktop Environments
---

### Post by kylegio on 2009-12-13
started after upgrade to 9.10, originally xserver would not start. gave a "fatal error" saying that "no screens found" could not find a resolution, this was shortly after the release of 9.10, i have not had leisure to investigate it further until today, i have updated/upgraded everything, still no avail. 

i then re-installed xserver/xorg/kubuntu-desktop completely, i thought that worked, after re-start i got the kubuntu login screen again (YAY), however now after providing my username/password instead of continuing on i am simply kicked out to the basic terminal login screen. from the terminal screen i can login and perform any terminal tasks i wish (updating/installing/removing packages, accessing files... etc) but i can not get a graphical interface to start properly. 


can anyone suggest a remedy?
if you require more information ask and i will provide what i can 

thanks
kyle

---

### Post by LuisGMarine on 2009-12-13
In the terminal you can try to re-configure X

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Zorael on 2009-12-13
If you have the terminal knowhow, you may want to check the log file for both X and KDM. They are at **/var/log/Xorg.0.log** and **/var/log/kdm.log** respectively.

If you are only used to working in a graphical interface, you could do this from a live CD, by mounting your root partition and then browsing to those files and opening them in a text editor.

Sometimes KDM's log contains errors that X's doesn't, so check both.

---

### Post by kylegio on 2009-12-15
the Xorg log is massive, i deleted it then made another attempt just to make sure only the most recent attempt was in the log, however again the log file is pretty extensive, i can attach it if any would think it useful, 

the final 2 lines of the log are
"Saw signal 11. Server aborting.
 ddxSigGiveUp: Closing log"


in the kdm log it ends with 
"Saw signal 11. Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11"

the kdm log also states in it

"X: unable to open wrapper config file /etc/X11/Xwrapper.config" (confirmed this file does not exist, i have reconfigured x11-common and now it exists, this line is not present in further error reports)

further down
"(EE) open /dev/fb0: no such file or directory"
"error setting MTRR (base=0x91000000, size = 0x00e00000, type 1) invalid argument (22)"


also i am comparing things to my desktop computer (true its not running kdm but i think my problem lies more with xserver so their configurations should be similar.i am noticing missing files, on my working desktop /etc/X11 has many sub folders and config files, on my non working laptop it only has "apps-defaults" "default-display-manager" "X" "Xwrapper.config", but is lacking things like "Xorg.config" among 10 or so other files that are on my working desktop. 


anyway any help would be appreciated, final note: when calling "startx" from the console, the screen flashes and i can see my kde background appear, then the screen goes black again and a grey box situated top left corner appears. it seems to be some sort of terminal, however i can not type in it and there is no output in it, it remains for about 3~5 seconds before the screen goes black again and i am back at the terminal with the "Saw signal 11. " error on screen.



thanks for the help

---

### Post by pixel :-) on 2009-12-15
i think, this command was abandoned some time ago, or it can't reconfigure the screen.
> sudo dpkg-reconfigure xserver-xorg

I can't decipher the logs. But in grub, it give you 3 choices, take the second, don't remember very well, something like "recovery mode". It will drop in a menu, chose the fix X, or default video mode, or something of the sort. You should be able to at least log in with some crappy resolution.

---

### Post by kylegio on 2009-12-15
> **pixel :-) said:**
> i think, this command was abandoned some time ago, or it can't reconfigure the screen.


I can't decipher the logs. But in grub, it give you 3 choices, take the second, don't remember very well, something like "recovery mode". It will drop in a menu, chose the fix X, or default video mode, or something of the sort. You should be able to at least log in with some crappy resolution.

i don't get the option to "fix X" or "Default video mode" when i select recovery mode from grub, i get a terminal style menu where i can arrow up or down through options, i have options like "normal boot", "terminal with networking", "fix broken packages (which doesnt help)"...etc

---

