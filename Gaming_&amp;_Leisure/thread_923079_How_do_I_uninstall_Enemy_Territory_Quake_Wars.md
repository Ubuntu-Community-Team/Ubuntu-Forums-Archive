---
title: "How do I uninstall Enemy Territory Quake Wars?"
date: 2008-09-18
forum: Gaming &amp; Leisure
---

### Post by swankyfb on 2008-09-18
I need help really bad please! my ET:QW crashes on startup when I updated so I need to re-install it. How do I uninstall this program? It will not show up in add/remove programs either. Thanks for looking.

---

### Post by leef on 2008-09-18
execute "wine uniinstaller"

If that doesn't work this might be useful.

do;
cd /home/user/.wine/drive_c/Program\ Files/

then do "ls" to see if ET:QW is located in that directory. If it's not their do
cd /home/user/.wine/drive_c

then do

find | grep Enemy

once you have found it "cd" to the directory that the install is located in and do;

rm -rf <name of Dir>

---

### Post by swankyfb on 2008-09-18
well, im not using wine. this is a _native linux_ client.

---

### Post by leef on 2008-09-18
> **swankyfb said:**
> well, im not using wine. this is a _native linux_ client.

lol, sorry I didn't know that :), still if you installed from source try "make uninstall" if you installed with apt-get try "apt-get remove <prog>". Sorry for the confusion.

---

### Post by swankyfb on 2008-09-18
lol its cool man, thanks.

---

### Post by eragon100 on 2008-09-18
It's a propietary game, hven't you heard of it? You *can't* install it with pt-get or from source!

"Uninstalling" it is very simple, but probably not necessary. To remove it, just delete the folder you installed it to, but to solve the problem, it should be enough to empty the .etqwcl directory in your home folder.

---

