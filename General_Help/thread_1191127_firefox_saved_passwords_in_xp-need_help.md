---
title: "firefox saved passwords in xp-need help"
date: 2009-06-18
forum: General Help
---

### Post by cjtaylor12 on 2009-06-18
Ok, so my pc with xp on it borked. Finally convinced the wife to just let me load ubuntu on it. Using the 9.04 live cd I am moving all our pics, documents, music, etc. to an external hard drive. What I need to know is, where are the saved passwords for firefox stored? Xp is totally unusable so I cant load firefox to access them. i need to know the location of the actual file itself so I can move that as well before I do a clean install of jaunty over the xp I cant use.

Any help would be greatly appreciated.

---

### Post by Celauran on 2009-06-18
C:\Documents and Settings\Username\Application Data\Mozilla\Firefox\Profiles\Some gibberish.default

Copy the entire "gibberish" directory somewhere safe. The first time you run Firefox on Ubuntu, it will create ~/.mozilla/firefox/different gibberish.

Remove everything in your Ubuntu gibberish directory and replace with the contents of your Windows gibberish directory. Everything will be there; passwords, bookmarks, cookies, preferences, the works.

---

### Post by Trebaruna on 2009-06-18
In the same directory that houses gibberish.default there's also a profiles.ini. Either take it with you or edit it to correspond to yourgibberish.default instead of the newly generated gibberish.

---

### Post by cjtaylor12 on 2009-06-18
OUTSTANDING! You saved me so much grief and headaches, I cannot even express my gratitude.

---

### Post by cjtaylor12 on 2009-06-18
ok, cant find the gibberish directory in 9.04. looked everywhere i could think of, just cant find it. any help?

---

### Post by michy99 on 2009-06-18
~/.mozilla/firefox/

---

### Post by VCoolio on 2009-06-18
You can use the xmarks plugin to synchronize bookmarks and passwords and then uninstall the plugin if you're satisfied and no longer need it.

---

### Post by cjtaylor12 on 2009-06-18
I'm utterly stupid today, I know its ~/.mozilla/firefox/ but I dont know where to find that. what directory is it under?

---

### Post by lisati on 2009-06-18
> **VCoolio said:**
> You can use the xmarks plugin to synchronize bookmarks and passwords and then uninstall the plugin if you're satisfied and no longer need it.
I think the latest version of xmarks can cope with passwords
> **cjtaylor12 said:**
> I'm utterly stupid today, I know its ~/.mozilla/firefox/ but I dont know where to find that. what directory is it under?
It's exactly where you said. If you're at a terminal, type in:```
cd ~/.mozilla/firefox/ 
```
If you're using nautilus (the usual Ubuntu desktop) you might want to use the "show hidden files" option

---

### Post by cjtaylor12 on 2009-06-18
see, that was my problem, the terminal. I haven't really used the terminal too much. Still learning. I tried it, but didn't put the cd in there. The show hidden files thing was what I needed. Problem totally solved. Thank you all for your help.

---

### Post by lisati on 2009-06-18
> **obr said:**
> I need a program that will let me burn mov files to a dvd? 

This new question might be answered here: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

For the saved passwords stuff, [xmarks]("http://xmarks.com") might be the way to go

---

### Post by lovinglinux on 2009-06-18
You can also use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to backup and restore profiles.

---

