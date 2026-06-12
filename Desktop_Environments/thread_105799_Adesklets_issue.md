---
title: "Adesklets issue"
date: 2005-12-19
forum: Desktop Environments
---

### Post by freakzilla on 2005-12-19
I installed adesklets from through synaptic and installed a couple desklets such as yab.  Everything looks good when i type the command "adesklets" in terminal.  Everything pops up and functions.  

When I go through "Session>Startup programs" or "Sessions>Auto Save changes" in an attempt to get adesklets to launch at start up, the program does not work on reboot.  Adesklets gets listed under the "current sessions" tab but none of the desklets show up.

---

### Post by art on 2005-12-19
Do you start up those desklets from their directories. What I did was to go to the directory, run ./"desklet_name", then restart the desklet right clicking on it. Then after next login it works. Tell me if this works. 
HTH

---

### Post by freakzilla on 2005-12-19
I installed adesklets through synaptic then created a directory in "home" called "adesklets_modules".  I then downloaded a couple desklets into folders under "adesklets_modules"  I then clicked on the "filename.py".  Edited the "config.txt" for each desklets.  

Okay, so I tried launching the individual desklets through terminal by ./"desklet_name", then restarted the desklets by right click.  But I still haven't had any success.  

Did i mess something up by originally installing the individual desklets via just clicking on the .py files in Nautilus.  Should i have installed each desklets through terminal?

---

### Post by art on 2005-12-20
i don't think the installation method would affect it. What I would do is to look in the .adesklets file, if there is any entries remove them, might as well remove the .adesklets file (it'll be recreated next time you run adesklets). Also remove the desklets you have (or only config files), and run from command line, from the directory they are installed in as ./desklte.py(that's the way they should be run according to their website). And then as I said before restart the desklet, include adesklet in the in the startup programs. Hope it works...

---

### Post by tigrez on 2005-12-21
Do you have tried gDesklets?
[www.gdesklets.org](www.gdesklets.org)
It's similar, and I found better desklets. 
Maybe the desklets are compatible...

---

### Post by freakzilla on 2005-12-22
I tried removing the .adesklets and config files.  Then install via ./desklte.py but no luck.  

I've tried gDesklets and its a nice program but adesklets is exactly what I like to use.

Upon searching the adesklets forums I think I may have some sort of flicker problem that effects adesklets.  Unforturnatly the explaination on their FAQ is not exactly geared toward the noob.

---

### Post by jasnix on 2006-11-06
don't know if you ever figured this out, but I believe what you need to do is run

adesklets --nautilus

---

