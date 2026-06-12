---
title: "Resolution"
date: 2005-01-31
forum: Desktop Environments
---

### Post by impel on 2005-01-31
Ok. I'm new to linux, but I think this ought to be obvious. I can't figure out how to change the resolution. I know changing it would require me to reboot the x server or something, but can't figure out how. I've ran various linux distros before with gnome and found it, but can't seem to find it on here.

help please

---

### Post by crane on 2005-01-31
Computer>System Configuration>Screen Resolution

Is that what you are talking about or are you talking about changing the XF86Config-4 file?

---

### Post by impel on 2005-01-31
ok. yes thanks man. somehow i totally missed how to get there. i thought i looked everywhere.


im just trying to add 1600x1200 and other resolutions to the config now, but for some reason it is only giving me 11**x7** and 55hz.

---

### Post by impel on 2005-01-31
i changed my config file to only contain 1600x1200 in the 24 section, rebooted and still have options of only 1152,1024,800,640. and 55hz. my video card and monitor support up to 2048, but i usualy use and want 1600x1200 or 1920x1440.

i think it has to do with my monitor not being set up right

i have sony gdm 500

---

### Post by crane on 2005-01-31
Yea adding different resolutions can be tricky. It was for me. I believe you have to change the refresh rates as well to add resolutions. Just be sure to not set it to high as it could ruin your monitor.

---

### Post by impel on 2005-01-31
any tips where to go for help. for maybe my specific monitor

---

### Post by mendicant on 2005-02-01
You can try finding the specs of your monitor online, if you don't have the manual.  You'll want the horizontal and vertical refresh rates.

You can also try getting read-edid from universe (not sure if it's only in hoary or if it's also in warty), and do:
% get-edid | parse-edid

---

### Post by dhonn on 2005-02-01
[QUOTE=impel]Ok. I'm new to linux, but I think this ought to be obvious. I can't figure out how to change the resolution. I know changing it would require me to reboot the x server or something, but can't figure out how. I've ran various linux distros before with gnome and found it, but can't seem to find it on here.

help please[/QUOTE]


You can reboot the x server by pressing **CTRL+ALT+BACKSPACE**

or in the terminal as root, run:  **telinit 3**.  then run:** telinit 5;exit**

**CTRL+ALT+BACKSPACE** is faster.

---

### Post by Wim Sturkenboom on 2005-02-02
[QUOTE=impel]any tips where to go for help. for maybe my specific monitor[/QUOTE]Find the horizontal and vertical refreshrates  in the manual of your monitor.
Next change the HorizSync and the Vertrefresh in the monitor section in */etc/X11/XF86Config-4*.

If you don't have the manual, you can (as said before) try to find it on the internet. 

Do you still have the 'driver' disk that came with the monitor? In that case you can have a look on it. The 'driver' is basically just an inf-file that contains config information for Windows. Open this inf-file in an editor and have a look. You should find something like```
[sm1109p.AddReg]
HKR,"MODES\2048,1536",Mode1,,"30-115,50-160,+,+"
HKR,,ICMProfile,0,"sm1109p.icm"
```The above is for my 21" monitor. The important numbers are 30-115 for HorizSync and 50-160 for VerRefresh.

Next option is that the monitor might have this info somewhere in its OSD.

Last option works if you still have a windows-installation and the monitor OSD can give you the used refreshrates in the OSD. Set the resolution in windows to e.g. 640x480 at the highest vertical refresh possible. Check on the monitors OSD what the horizontal refresh rate is. Repeat for all other resolutions. Write down the refresh rates and use the highest vertical refresh as well as the highest horizontal refresh that you find.

---

### Post by Buffalo Soldier on 2005-02-02
You can try running this command in terminal:```
dpkg-reconfigure xserver-xfree86
```But I don't recommend this if you're not really sure what configuration to change/not to change.

---

