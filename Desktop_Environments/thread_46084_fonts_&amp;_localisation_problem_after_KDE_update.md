---
title: "fonts &amp; localisation problem after KDE update"
date: 2005-07-03
forum: Desktop Environments
---

### Post by Kuolio on 2005-07-03
Hi o/

I updated KDE to version 3.4.1 using repos I found on this forum, and after that some of my letters ( ä-ö-å  a.k.a scandic-letters) on the finnish layout (iso8859-15 or [email]fi_FI@euro.UTF[/email]8 or fi_FI.UTF8 ) haven't worked correctly.

Or, i should say that they are working in some parts of KDE, but menunames and controllcenter only display boxes instead of those letters (öäå). And if i try to change the menunames to use äöä just by typing them in meuedit, i get borked letters A€O€ etc. Programs mostly show them correctly, except for Terminal wich stopped showing them right when I updated to 3.4.1. Webpages and such work.

Still, i have some menuentrys in K-menu using scandic-letters correctly, "Change User / Vaihda Käyttäjä" and few programnames and descriptions like in multimedia "Soundmixer / Äänimikseri" show their scandic letters correctly. In Controllcenter only the menunames and headlines are missing scandic letters, but they do work on the text-part. I seriously dont have no idea whats going on. 

I have tried to reconfigure my locales, changing between finnish-iso and UTF8 with dpkg-reconfigure locales, but they havent worked. Also i seem to be missing some fonts, when i tried to look into controllcenters font-list, it doesnt show any fonts. I used synaptic by searching "fonts" and got a huge list, where i downloaded and (re-)installed some fonts and fontpacks but i didn't find any KDE spesific font-packs.

Anyone have any ideas?  ](*,)

---

### Post by Lord Illidan on 2005-07-03
I believe you should have kept to where you where..an odd point (1,3,5,7,9) release in the world of Linux is generally more buggy than an even point release. Can you revert back to where you were before, and then upgrade to 3.4.2?

---

