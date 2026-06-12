---
title: "wolfenstein enemy terretory halp pl0x"
date: 2010-07-25
forum: Gaming &amp; Leisure
---

### Post by simieon on 2010-07-25
[http://www.truecombatelite.com/tce.php?page=downloads](http://www.truecombatelite.com/tce.php?page=downloads)

downloaded wolfenstein enemy terretory from the link above, with the goal of playing true combat elite on my newly converted to linux. but being a silly long time windows consumer i have no clue how to actually install the file, my lazyness have lead me to a /headdesk situation trying to figure out how, so here i am politely asking for a guide link or similar to help me get it working. thanks in advance, yours truly.

ps. if you can help me out here, ill invite you over for milf and cookies!

---

### Post by louis--taylor on 2010-07-25
> [IMG]http://www.truecombatelite.com/images/random/weticon.gif[/IMG][**Wolfenstein Enemy Territory Full (with 2.60 Patch)**]("http://www.truecombatelite.com/files/ET_v2.60_Linux.run.gz")
*(ET_v2.60_Linux.run.gz  258.41 mb 21-Mar-2005)*

Decompress this?

---

### Post by simieon on 2010-07-25
yup, exactly, but i cant decompress it.

gzip: /home/odie/Hentede filer/ET_v2.60_Linux.run.gz: not in gzip format


is the result im getting when trying to decompress it, i thought gz was gzip files. do i need another decompressor or something to make it work, or just get the windows release and do it through wine?

---

### Post by Technophobia on 2010-07-25
Try this

open a terminal with a happy face on and navigate to the location of your file and run

chmod +x ET_v2.60_Linux.run.gz
sudo ./ET_v2.60_Linux.run.gz

and the same for the TCE file when you get it.

It seems the gz just means the installer is using compression within itself, which is very misleading.

---

### Post by collinp on 2010-07-25
```
gunzip -d /home/odie/Hentede\ filer/ET_v2.60_Linux.run.gz && chmod +x /home/odie/Hentede\ filer/ET_v2.60_Linux.run && sudo /home/odie/Hentede\ filer/ET_v2.60_Linux.run.gz
```The first command decompresses it, the second command sets the installer as executable,  the third command runs the installer as the root user (it has to be ran as root, from my memory).

---

### Post by simieon on 2010-07-25
chmod: kan ikke tilgå 'ET_v2.60_linux.run.gz': No such file or directory
           (cannt acces: directly translated)

this would mean i should use a $home\username\downloads (space) before the command right? to tell the terminal where to find the file?

and thanks a lot :D  /bow

---

### Post by collinp on 2010-07-25
> **simieon said:**
> chmod: kan ikke tilgå 'ET_v2.60_linux.run.gz': No such file or directory
           (cannt acces: directly translated)

this would mean i should use a $home\username\downloads (space) before the command right? to tell the terminal where to find the file?

and thanks a lot :D  /bow

I changed a few things in the command, try it now.

---

### Post by simieon on 2010-07-25
gzip: /home/odie/Hentede filer/ET_v2.60_Linux.run.gz: not in gzip format


besides from the obvious mistake of actually posting my username in a place where my ip is accessible without connecting through a vpn or proxy. i belive i am pretty close to calling this as a bad release from the developer. and use the release for windows through wine download is running as i type. 

i appreciate the help very much, and if you find this interesting im ofc willing to get this working the proper way, contact developers etc. if not, i really appriciate the help and is gonna take my first venture into wine which i will probably be needing for my audio software anyway :D

/bow

---

### Post by Technophobia on 2010-07-25
!THERE IS NOTHING TO EXTRACT!

simieon, don't give up yet. Simply run the following command from your terminal and you should be presented with a colorful terminal based installer from the 1980s.

chmod +x ~/"Hentede filer/ET_v2.60_Linux.run.gz"; sudo ~/"Hentede filer/ET_v2.60_Linux.run.gz"

"chmod +x" marks the file so that you can run it. You can do the same thing on the desktop by right clicking the file and going to properties and then to permissions.  'sudo ~/"Hentede filer/ET_v2.60_Linux.run.gz"' runs the installer as the superuser, so that it can install to "/usr/local/games", which is a common location for game installs.

---

### Post by simieon on 2010-07-25
last command line worked, installer running now. thanks a lot :D

/edit   thanks for explaining the terminal commands to me in your edit. "give a man a fish, and he eats for a day. teach a man to fish, and he eats everyday"

---

