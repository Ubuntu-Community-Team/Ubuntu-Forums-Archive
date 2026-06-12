---
title: "how to create a firefox backup"
date: 2009-01-25
forum: General Help
---

### Post by Kain000 on 2009-01-25
DOes anyone know how to make a backup for firefox of all your settings and bookmarks, with passwords?  Im migrating back to 32 bit ubuntu and want all my stuff still there.

---

### Post by b0b138 on 2009-01-25
Well your firefox profile is located at /home/user/.mozilla/firefox/xxxxxxxx.default/  Copy that folder and the profiles.ini file. Though I don't know if there would be any problems going from 64bit to 32bit.

---

### Post by Kain000 on 2009-01-25
thanks for the tip.  so I guesing that I would just save that folder, and replace the new one with it.

---

### Post by Cope57 on 2009-01-25
[Foxmarks]("http://www.foxmarks.com/") is great for bookmarks, but as for the settings, I am not to sure.

---

### Post by JasonR on 2009-01-25
FEBE!  

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

Jason

---

### Post by Kain000 on 2009-01-25
> **JasonR said:**
> FEBE!  

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

Jason

NICE!!!  great call this is perfect, and better than just a backup because I hate having to remember or email myself links to sites from my laptop to my desktop.

-Awesome

---

### Post by mb_webguy on 2009-01-26
You don't need FEBE to tranfer your bookmarks from one computer to another...  Just export them to an html file (using the "Import and Backup" button on the Organize Bookmarks window), and then import them on the other computer.

---

### Post by adamlau on 2009-01-26
No need to export bookmarks if moving from 64 to 32, simply back up 'places.sqlite'.

---

### Post by Ahadiel on 2009-01-26
You may also want to consider putting /home on a separate partition.

---

### Post by hyper_ch on 2009-01-26
> **b0b138 said:**
> Well your firefox profile is located at /home/user/.mozilla/firefox/xxxxxxxx.default/  Copy that folder and the profiles.ini file. Though I don't know if there would be any problems going from 64bit to 32bit.
I'd just make a copy of all of ~/.mozilla

> **Ahadiel said:**
> You may also want to consider putting /home on a separate partition.
Why?

---

### Post by mb_webguy on 2009-01-26
Putting /home on a separate partition makes the upgrade or reinstallation process much easier, since you don't have to worry about losing your data or settings.  Ubuntu can live happily on an 8 to 10GB partition, which means you can devote the rest of the drive to your /home directory.  Then, the next time you reinstall (such as if you want to do a clean installation of a new version of Ubuntu, rather than an upgrade), then you automatically keep your documents, movies, music, and other files, as well as all of your personal settings located in those hidden files and folders in your home directory.

You can actually put any directory on its own partition, and it's common for servers to have separate partitions for /var and /usr in addition to /home, but for a personal computer, a separate /home is pretty much the only one that would be useful.

---

### Post by hyper_ch on 2009-01-26
> **mb_webguy said:**
> Putting /home on a separate partition makes the upgrade or reinstallation process much easier, since you don't have to worry about losing your data or settings.
I disagree here. Having /home on a seperate partition will not prevent you from losing data. Only backups do. For reinstallation it might offer more convenience but IMHO not by much.

> **mb_webguy said:**
> Then, the next time you reinstall (such as if you want to do a clean installation of a new version of Ubuntu, rather than an upgrade), then you automatically keep your documents, movies, music, and other files, as well as all of your personal settings located in those hidden files and folders in your home directory.
But what is the reason to do a clean install? IMHO in a clean install I don't want to just copy all the configs I had before, otherwise what would I reinstall for?

---

### Post by halovivek on 2009-01-26
> **hyper_ch said:**
> I disagree here. Having /home on a seperate partition will not prevent you from losing data. Only backups do. For reinstallation it might offer more convenience but IMHO not by much.


But what is the reason to do a clean install? IMHO in a clean install I don't want to just copy all the configs I had before, otherwise what would I reinstall for?

I really accept this. Regular backups will do a system safe.

---

### Post by mb_webguy on 2009-01-26
I wasn't saying that it not still good to backup your data -- you should always have a backup of any data you don't want to lose, no matter what you're doing.  But having a separate home partition does make reinstallation much easier, since if you do it correctly, you don't have to restore the backup.  

Also, a clean installation other than your home directory can definitely be a good thing, since there are plenty of ways an upgrade can cause quirks in your system that have nothing to do with the preferences in your home directory.  I speak from experience here -- I upgraded from Hardy to Intrepid, and had several problems pop up.  So I did a clean install of Intrepid with the exception of my existing home partition, and those problems went away.

---

