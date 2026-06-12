---
title: "Can't install themes"
date: 2009-12-29
forum: Desktop Environments
---

### Post by marticc on 2009-12-29
Hello,


I have just re-installed Ubuntu 9.10 (I used to have it inside my windows Vista partition -wubi-, but, as I had to format my Vista OS to install Windows 7, i decided to re-install ubuntu in an independent partition ). Before formatting my laptop I made a backup of my old home folder to save my Firefox settings and some personal files in a USB hard driver (sudo cp -a /home /media/backup) . After reinstalling Ubuntu 9.10 i reinstalled that folder (sudo cp -a /media/backup /). 

I used to have a theme I really liked (Nouve XT 1.7) and I hoped that reinstalling my old home folder was going to be enough so that I could keep using that theme

After reinstalling I tried to change the  Ubuntu default icons to use the Nuove XT icons (preferences/appearance preferences/ themes/ custom/icons and I chose Nuove XT 1.7) the desktop started to shake (it was a crazy and strange thing I had never seen before) and I had to undo the icons change 

After that I tried to reinstall the theme and I wasn't able to do that. I downloaded the theme, and I opened  the appearance preference window. I went to the theme tab (where I can see the themes available -funnily enough I could not see Nuove XT Theme but if I clicked  on custom/icons, I could see the Nuove XT icons folder), I clicked on "install", I chose the Nuove XT tar.gz, and when I clicked on "open" I got the following error message: "Nuove XT can't be installed, you can't move a directory over another directory" (please note that I am trying to translate a message that was originally written in Spanish into English, and my English is not very good).

I tried using emerald manager, but when I tried to import the Nuove XT, the emerald manager could not see it in the folder where the Nuove XT tar is located.

I hope you can help to install this theme.

Thanks.

---

### Post by marticc on 2009-12-30
Doesn't anyone know a solution for this problem?.

I would be really grateful if you could help me.

---

### Post by marticc on 2009-12-31
Hi, I 'd like to say that I finally managed fix it. I deleted the NUOVEXT folder located in /home/usuario/.icons, and I reinstalled the theme. Now it works great.

---

