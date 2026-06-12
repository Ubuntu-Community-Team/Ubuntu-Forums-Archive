---
title: "Converting a printer driver file to PPD"
date: 2006-04-02
forum: Desktop Environments
---

### Post by JDavid5381 on 2006-04-02
Does anyone know how to convert a printer driver file such as this one- z600cups-1.0-1.gz.sh- into a PPD file so that I can install the driver. I need it because I have Dell 924 printer that came with my computer, however the only driver for it is for Windows :(  But I found out through Linux forums that the printer is identical to the Lexmark Z615, and thats the driver I need to install because its not included in the Ubuntu package of printer drivers. Any help would be much appreciated. Thanks.

-James

---

### Post by beefsprocket on 2006-04-02
Take a look at this howto: [http://ubuntuforums.org/showthread.php?t=49714&highlight=z600]("http://ubuntuforums.org/showthread.php?t=49714&highlight=z600")

---

### Post by JDavid5381 on 2006-04-02
Thanks for the help and pointing me in the right direction, however, those postings were for Hoary, I'm using Breezy.  Everything worked out fine in the Terminal until I got the part using the command "alien,"  the computer responded
bash: alien: command not found

does anyone know of newer "how to" on this topic?  Or what the quivalent for the command for "alien" is on Breezy?

Thanks again in advance :)

James

---

### Post by beefsprocket on 2006-04-02
My mistake. I didn't mention that that howto works on breezy as well as hoary. For alien, all you need is to sudo apt-get install alien. I think that you can avoid problems that might crop up if you instead do an alien -i "rpmnamehere" instead of -t. This converts the rpms directly to .deb files and installs them, bypassing the manual installing of the gzip files.

---

