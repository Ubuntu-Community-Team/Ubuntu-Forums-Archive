---
title: "xmame works, gxmame can't find roms"
date: 2005-08-17
forum: Gaming &amp; Leisure
---

### Post by Refund on 2005-08-17
I can load roms into xmame fine, but I want gxmame to work for obvious reasons

it detects xmame fine, but when I point it towards the roms, it fails to see anything (and put it into the list)

I've looked everywhere, and I can't find the problem, I've tried extracting the .zip's moving directories all over the place, and nothing works.

---

### Post by lol on 2005-08-17
I had exactly the same problem, but to be honest, I tried so many things I don't really remember what solved the issue... :(
If I am not mistaken though, it may be a bug with your current version of gxmame. I am currently using the version 0.35beta2 (which is not available from gxmame home page... try google).

---

### Post by atilasendil on 2005-09-01
It's working, it's working :-)
I had tried the .34b as .deb from the original site;
then the source of the same;
no directory recognition;
at last I also googled for .35beta2 and installed directly from the .deb and am so happy;

I guess it just will take some time for me to unrar 700MB*15 CD archives of ROMS to /usr/share/games/xmame/roms/ :-)

---

### Post by andlinux21 on 2006-02-03
THANKS I cant wait to get home and test this. I can play roms fine with xmame but it wont play from the hard drive only for a CD a made i wish i could drop the roms to the laptop hard drive and play them from there

---

### Post by 8bit on 2006-02-19
[QUOTE=atilasendil]It's working, it's working :-)
I had tried the .34b as .deb from the original site;
then the source of the same;
no directory recognition;
at last I also googled for .35beta2 and installed directly from the .deb and am so happy;

I guess it just will take some time for me to unrar 700MB*15 CD archives of ROMS to /usr/share/games/xmame/roms/ :-)[/QUOTE]


I had the same problem and followed your instructions and now it's working.

---

### Post by ringmaster on 2006-08-06
I don't know if this helps anybody, in my case the frontend was kxmame (I installed xmame and xmame-common from ubuntu repositories previously) and the roms were capitalized (from winbugs) so I tested to change one game to small letters and IT WORKED! (I did audit all games on the menu) so in terminal I went to the roms directory and I did:

for i in *.*; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

windows doesn't have this possibilities!! I love those powerfull commands!!

After this I audit again and voilá! +1000 games detected!!

I don't now if the problem is the coding of my filesystem  (reiserfs) as I am spanish (excuse me my gramathical errors) and I have problems with locales (I tried to resolve them with how-tos without success).

---

### Post by gregory_ on 2008-02-16
:))))Yes gxmame 0.35beta2 worked
(had the same problem)

---

### Post by jonerich on 2010-11-22
> **ringmaster said:**
> I don't know if this helps anybody, in my case the frontend was kxmame (I installed xmame and xmame-common from ubuntu repositories previously) and the roms were capitalized (from winbugs) so I tested to change one game to small letters and IT WORKED! (I did audit all games on the menu) so in terminal I went to the roms directory and I did:

for i in *.*; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

windows doesn't have this possibilities!! I love those powerfull commands!!

 After this I audit again and voilá! +1000 games detected!!

I don't now if the problem is the coding of my filesystem  (reiserfs) as I am spanish (excuse me my gramathical errors) and I have problems with locales (I tried to resolve them with how-tos without success).


Thank you so much!!!!!!! The Roms have to be in lower case i did the above and everthing is working!!!!

---

### Post by Perfect Storm on 2010-11-23
Necromancing.


Thread closed.

---

