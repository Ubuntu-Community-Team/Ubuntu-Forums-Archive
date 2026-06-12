---
title: "compiz-fusion error?"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by dynamethod on 2007-09-13
hey i installed compiz fusion, once i typed in compiz --replace into the terminal i got this message:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

i checked that my ATI X800 XT AGPx8 could work with direct rendering:

glxinfo | grep direct
direct rendering: Yes

is compiz fusion just not going to work with my ATI card? ive tried so many different ways and how-to's to try and get it working, but nothings doing it :S

---

### Post by coloured on 2007-09-13
what method are you using to install compiz? 
I build mine using this script on feisty and works without any problems - it also seems much faster than from the .debs  [=http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz+fusion](=http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz+fusion)

make sure you uninstall all compiz stuff from synaptic before using this script. btw this script builds the latest stuff, because it uses git. the script also allows you to uninstall if you dont want it anymore.

there is also something called compiz-icon which puts a nice little icon in the notification area - and makes it easy to start (also puts a program group in my gnome menu).

Jurgen

---

### Post by dynamethod on 2007-09-13
using the script now, thanks for the link :)

however is it trying to install KDE onto my desktop? im using gnome btw

---

### Post by smartboyathome on 2007-09-13
> **dynamethod said:**
> using the script now, thanks for the link :)

however is it trying to install KDE onto my desktop? im using gnome btw

Remember to completely uninstall any previous install.

---

### Post by dynamethod on 2007-09-13
well if your referring to KDE, i never had KDE in the first place, i dont want it either, im just watching it install KDE.. it asked me if i had the KDE library, i chose 'no' and it installed 270megs of KDE :S

i need to have KDE in order to use compiz-fusion?

---

### Post by dynamethod on 2007-09-13
wtf, its just mixed up gnome with kde ffs, so now how do i remove kde? as for the CF, still not working :S, however i guess i got a hybrid gnome/KDE desktop now lol

---

### Post by coloured on 2007-09-13
when you run the script it will prompt you to ask if you have any kde libraries - answer no if you use gnome.

Rerun the script and select to uninstall compiz. then rerun it again and dont install kde libraries.

btw - I run gnome on my laptop (gnome kicks the pants off of kde) - and I am running compiz fusion and dont have any kde stuff installed by the script.
compiz runs flawlessly never crashes and no problems at all.

---

### Post by coloured on 2007-09-13
oh yeah - choose to install the compiz-icon :)

---

### Post by dynamethod on 2007-09-13
ya i love gnome alot more than kde,  i can get the compiz icon thing straight, but now how do i acutally uninstall KDE itself? compiz fusion just refuses to work on my computer some reason i give up now, but id really like to remove KDE i cant afford the diskspace for it :S

---

### Post by coloured on 2007-09-13
did the kde stuff come down when you installed compiz using that script? if so just rerun the script and choose to uninstall.

---

### Post by dynamethod on 2007-09-13
ya i ran it again but it didnt uninstall the KDE desktop enviroment :S

theres 270mges of kde here now ive got duplicates of everything that i already need but in kde, 
im looking through synamptic now to remove it but im not so confident some of these files here look like they could stuff up my system, im not as confident with linux as yet,

---

