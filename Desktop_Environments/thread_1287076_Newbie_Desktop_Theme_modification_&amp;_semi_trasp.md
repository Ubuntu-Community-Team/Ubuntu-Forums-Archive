---
title: "Newbie Desktop Theme modification &amp; semi trasparent console"
date: 2009-10-09
forum: Desktop Environments
---

### Post by Kaizzer on 2009-10-09
hi.. im kind of new to this so please forgive me if this sounds dum

ive dowloaded a theme from some site ... (Sickness in black) and i like it a lot .. but .. in this particular theme .. openoffice speadsheets .. are shown black color also ..wich is a problem to me couse i use a lot of them.. 

is there a way to change that ? i tryed to modify the default collors in the spreadsheet appl .. but .. its not working fine.. looks like the theme is taking care of the looks of the openoffice.. 
is there a way to change that ? 

i would like also that my console windows .. were semi-transparent .. how can i achive that ?? 

thanks in advace..

---

### Post by undecim on 2009-10-09
For the open office thing, put this in a file in your home directory called "ooffice"
```
#!/bin/bash
env GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/bin/ooffice "$@"
```

then, move it to /usr/local/bin/ and make it executable with these commands:
```
sudo mv -n ~/ooffice /usr/local/bin
sudo chmod a+x /usr/local/bin/ooffice
```

You can do this with any other program you like. Just make sure you change the "/usr/bin/ooffice" to the path of the program you want to change, and change the name of the file you save to the name of the program. If you don't know the path of a program, use the "which" command (ex. "which ooffive" outputs "/usr/bin/ooffice"

for the console windows, you can set transparency from the "Background" tab in Edit -> Profile Preferences

---

### Post by Kaizzer on 2009-10-13
thanks.. undecin... i'll try that and post my outcome here.. 
regards.

---

### Post by Kaizzer on 2009-10-13
> **undecim said:**
> For the open office thing, put this in a file in your home directory called "ooffice"
```
#!/bin/bash
env GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/bin/ooffice "$@"
```then, move it to /usr/local/bin/ and make it executable with these commands:
```
sudo mv -n ~/ooffice /usr/local/bin
sudo chmod a+x /usr/local/bin/ooffice
```
for the console windows, you can set transparency from the "Background" tab in Edit -> Profile Preferences

ive done exactly what you post but ..when im using the theme... and openofice.. still shows the wrong colors.

is it necessary to reboot ? 

ill try that .now.

---

### Post by Kaizzer on 2009-10-13
nup ..  reboot doesnt seems to work either .. 
:(

---

### Post by Kaizzer on 2009-10-13
Ok .. just went reviewing another thread and found a solution that works..im not quite sure why this works .. and udecin's solution doesnt .. but still .. here is the link 

[http://ubuntuforums.org/showpost.php?p=5062879&postcount=7](http://ubuntuforums.org/showpost.php?p=5062879&postcount=7)

---

