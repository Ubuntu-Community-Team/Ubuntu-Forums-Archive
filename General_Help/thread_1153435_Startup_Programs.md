---
title: "Startup Programs"
date: 2009-05-08
forum: General Help
---

### Post by Muscovy on 2009-05-08
I'm trying to select a program (boinc) to open upon start. I'm really new to Linux. What file would I be selecting in the 'add startup' menu?

---

### Post by Tipped OuT on 2009-05-08
Just type in the "command" box the raw name of the application. For example, if I want cairo dock to start automatically on start up, then I would type "cairo-dock". Just find out what the command is to start it up from terminal. I believe if you right click the application launcher it'll have it there.

---

### Post by Muscovy on 2009-05-08
Thanks, found the command!

---

### Post by Muscovy on 2009-05-08
Is there a way to boot it in the second desk? Anything that leaves the workspace clear, while still running boinc.

---

### Post by MFinkel on 2009-05-10
Hi, I sort of have a similar problem, except I am way new to Ubuntu. I have downloaded BOINC to the desktop and no matter what I try I can not open it. sudo apt-get and the boinc-client boinc-manager do not work and I trid it with boinc-client, boinc-manager and still no joy! Also, I checked and it is not listed in system tools. Any ideas? Thanks.

---

### Post by MFinkel on 2009-05-10
I am running Ubuntu 8.04.1 LTS Desktop Edition.

---

### Post by oldos2er on 2009-05-10
> **MFinkel said:**
> Hi, I sort of have a similar problem, except I am way new to Ubuntu. I have downloaded BOINC to the desktop and no matter what I try I can not open it. sudo apt-get and the boinc-client boinc-manager do not work and I trid it with boinc-client, boinc-manager and still no joy! Also, I checked and it is not listed in system tools. Any ideas? Thanks.
  Open a terminal, run
```
cd Desktop
sh ./boinc.name.of.file.sh
```
 I can't recall the file name, so replace boinc.name.of.file with whatever it is.

 Running the script will create a boinc directory, so once that's done, "cd" into the boinc directory and run 
```
./run_client
```
to set it up.

---

