---
title: "NWN Segmentation Fault"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by Crank Parity on 2008-12-29
Hello,

I've recently upgraded from Ubuntu 8.4 to 8.10, and now when I try to run NWN I get a segmentation fault. I've looked at a few other threads and verified permissions and my installation, and everything seems to be in order. I've also tried removing the ./lib: from the script, and deleting the lib directory, but both did not work.

I've ran the strace command with the following result: [http://pastebin.com/m2457c387](http://pastebin.com/m2457c387)

Anybody have any ideas as to what's going on, and how I can fix it?

---

### Post by fusa on 2009-01-01
I have been having the same problems also.  I tried following the Bioware instructions and the instructions here to run the game.  I keep getting a segmentation fault error, even after removing ./lib from the "export LD_LIBRARY_PATH=" portion of nwn.

---

### Post by lasal on 2009-01-01
> **fusa said:**
> I have been having the same problems also.  I tried following the Bioware instructions and the instructions here to run the game.  I keep getting a segmentation fault error, even after removing ./lib from the "export LD_LIBRARY_PATH=" portion of nwn.

I have had these problems, the only way I have found is a clean install (not an upgrade), making sure I have the 32bit libraries on a 64bit system and removing ./lib from the "export LD_LIBRARY_PATH="

---

### Post by fusa on 2009-01-02
I found the problem, /texturepacks/XP2_GUI.erf was names xp2_gui.erf  Fixinstall didn't fix the name.  Also I added to nwn.ini:

[Alias]
HD0=/path/to/install
OVERRIDE=override
TEMP=temp
MODULES=modules
LOGS=logs
LOCALVAULT=localvault
DMVAULT=dmvault
SERVERVAULT=servervault
TEMPCLIENT=tempclient
SAVES=saves
CURRENTGAME=currentgame
HAK=hak
PATCH=patch
NWMFiles=nwm
AMBIENT=ambient
MOVIES=movies
MUSIC=music

---

