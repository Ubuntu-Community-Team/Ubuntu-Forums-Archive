---
title: "need help for kxmame"
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by ccrabbit on 2007-10-16
i am a new kubuntu user and i just installed the kxmame by Add/Remove Program.

And after i installed i found that i couldn't play the games. because when i created a folder (for example /home/name/roms) and put the roms (.zips) in the folder , it wouldn't detect them, and it said that they   were not mame/mess executable even though i change the path in the settings.

therefore if anybody could tell how to configure the software? As well if there is a tutorial step by step...

thanks a lot.

---

### Post by DoktorSeven on 2007-10-16
You need one of the Xmame packages installed as well (it's in Universe or Multiverse -- search if you don't know how to add these repositories).  Unlike the Windows version of MAME, kxmame is not a self-contained version of MAME, it's just a front-end for the xmame program.  After it's installed you can point kxmame to the xmame program you installed (in /usr/games) with Settings->Directories->kxmame Paths->Xmame/XMess executables (don't forget to use Add after browsing) and there will be a separate setting to point to your MAME rom directory (MAME/Mess basic paths->Mame ROMS path, again, hit Add after browse).

You will have to tell kxmame to build the ROM database with Settings->Rebuild game list (basically, it has to ask xmame what games it supports), then refresh your game library with View->Refresh (asking kxmame what games you have in your directory).

---

### Post by sherl0k on 2007-10-16
The problem with the version of kxmame in the repo is that xmame is horribly outdated, and kxmame doesn't support sdlmame, which stays updated.

There's a svn version of kxmame available on their sourceforge page which DOES support sdlmame, I'd suggest compiling that from scratch.

---

### Post by bcdeck on 2007-10-24
An issue I ran into was that the "add/remove" apparently function didn't install all kxmame modules, not to mention xmame. 

Went to synaptic package manager, searched xmame and installed, then pointed kxmame to xmame in the prefs and all worked fine.

---

### Post by Failtacular on 2008-10-23
> **DoktorSeven said:**
> You need one of the Xmame packages installed as well (it's in Universe or Multiverse -- search if you don't know how to add these repositories).  Unlike the Windows version of MAME, kxmame is not a self-contained version of MAME, it's just a front-end for the xmame program.  After it's installed you can point kxmame to the xmame program you installed (in /usr/games) with Settings->Directories->kxmame Paths->Xmame/XMess executables (don't forget to use Add after browsing) and there will be a separate setting to point to your MAME rom directory (MAME/Mess basic paths->Mame ROMS path, again, hit Add after browse).

You will have to tell kxmame to build the ROM database with Settings->Rebuild game list (basically, it has to ask xmame what games it supports), then refresh your game library with View->Refresh (asking kxmame what games you have in your directory).

Step by step instructions, please?

---

### Post by disturbedite on 2008-10-24
> **sherl0k said:**
> There's a svn version of kxmame available on their sourceforge page which DOES support sdlmame, I'd suggest compiling that from scratch.
DoktorSeven made a deb package of it already...

---

