---
title: "Eternal Lands Install Trouble"
date: 2007-02-25
forum: Gaming &amp; Leisure
---

### Post by timjayko on 2007-02-25
Hello Ubuntu forums... I have been trying to install this MMORPG called eternal lands and am very new to ubuntu and linux as well... I am I think at the step where I attempt to run the file to start the game but when I attempt this the following error occurs in my command prompt 

$ ./el-133.x86.linux.static
I/O warning : failed to load external entity "languages/en/strings/console.xml"
I/O warning : failed to load external entity "languages/en/strings/console.xml"
I/O warning : failed to load external entity "languages/en/strings/errors.xml"
I/O warning : failed to load external entity "languages/en/strings/errors.xml"
I/O warning : failed to load external entity "languages/en/strings/help.xml"
I/O warning : failed to load external entity "languages/en/strings/help.xml"
I/O warning : failed to load external entity "languages/en/strings/options.xml"
I/O warning : failed to load external entity "languages/en/strings/options.xml"
I/O warning : failed to load external entity "languages/en/strings/spells.xml"
I/O warning : failed to load external entity "languages/en/strings/spells.xml"
I/O warning : failed to load external entity "languages/en/strings/stats.xml"
I/O warning : failed to load external entity "languages/en/strings/stats.xml"
I/O warning : failed to load external entity "languages/en/strings/titles.xml"
I/O warning : failed to load external entity "languages/en/strings/titles.xml"

please help thanks

---

### Post by Kubunteando on 2007-04-22
Have you configured the datadir in the el.ini file.
That entry needs to point to the folder where you installed the game.
This is mentioned in the installation comments in the official web site.

If you have run the game already there is already a copy of the el.ini file in the .elc folder in your home directory. You need to perform the change there as well. I had to do so when running the version 1.3.3.

Good luck.

---

