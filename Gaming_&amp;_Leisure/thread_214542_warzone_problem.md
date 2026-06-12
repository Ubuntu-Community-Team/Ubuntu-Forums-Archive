---
title: "warzone problem"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by shugie on 2006-07-12
Warning: Using colour depth of 16 instead of 24.
Error: SDL_SetVideoMode failed (Couldn't find matching GLX visual

Does anyone know what this means? I have tried installed 

libsdl1.2-debian
libsdl1.2-debian-asla
libsdl-gfx1.2-4

I have also tried to reconfigure xorg.conf to make sure it includes 24-bit color.

---

### Post by shugie on 2006-07-13
Ok, I got by that. Now I get 

./warzone.bin: symbol lookup error: ./warzone.bin: undefined symbol: alutLoadWAVMemory

Any help?

---

### Post by viciouslime on 2006-07-18
Since so many people are having problms with this game, I have made some deb files. They are available on my site ([http://www.viciouslime.co.uk/]("http://www.viciouslime.co.uk/") under downloads/linux/games. You'll need both warzone2100 and warzone 2100 -data.

Please let me know if they work for you.

---

### Post by NeutrinoX on 2006-07-24
> **viciouslime said:**
> Since so many people are having problms with this game, I have made some deb files. They are available on my site ([http://www.viciouslime.co.uk/]("http://www.viciouslime.co.uk/") under downloads/linux/games. You'll need both warzone2100 and warzone 2100 -data.

Please let me know if they work for you.

Same problem. Nope... no help... tried from the packages you're providing, and tried to compile by myself. At least I got to the menu, but when I try to start a game, it just closes. Seems like Warzone 2100 doesn't like Ubuntu...

---

### Post by Perfect Storm on 2006-07-24
Try my howto compiling warzone 2100: [http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13](http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13)

---

### Post by NeutrinoX on 2006-07-24
> **Artificial Intelligence said:**
> Try my howto compiling warzone 2100: [http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13](http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13)

That's the howto I used to compile it (Great work BTW! ;) ) but still no luck. I'll just try to check everything again and try to find what I'm doing wrong. This is a really good game, and it's mostly the only thing I miss from Windows.

---

### Post by Perfect Storm on 2006-07-24
What graphic card do you have? and is it setup correctly?

---

### Post by NeutrinoX on 2006-07-25
Ummm... gotta try again. My graphics card is a ATI Radeon 9200 SE, and I'm going to use the steps shown here [http://www.genbeta.com/archivos/2005/04/29-aceleracion-3d-para-tarjetas-.php](http://www.genbeta.com/archivos/2005/04/29-aceleracion-3d-para-tarjetas-.php) (Spanish) [http://translate.google.com/translate?u=http%3A%2F%2Fwww.genbeta.com%2Farchivos%2F2005%2F04%2F29-aceleracion-3d-para-tarjetas-.php&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.genbeta.com%2Farchivos%2F2005%2F04%2F29-aceleracion-3d-para-tarjetas-.php&langpair=es%7Cen&hl=es&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools) (Google-translated to English. Notice that "I sweat" there = sudo)

---

### Post by viciouslime on 2006-07-25
May I suggest you try [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") This is the official guide from the wiki, might be easier than using a translated one from elsewhere. Though not as humourous (sudo = I sweat, that's great :-P ).

---

### Post by NeutrinoX on 2006-07-27
> **viciouslime said:**
> May I suggest you try [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") This is the official guide from the wiki, might be easier than using a translated one from elsewhere. Though not as humourous (sudo = I sweat, that's great :-P ).

Ya, okay. :p (I'm spanish native, and found it specially amusing as well). Followed the wiki, step by step and... wait! There's something. Well, at least Warzone 2100 runs, but painfully slow... and seems there's something weird about the driver, because some games that went perfectly well, specially ioquake3 ( [http://icculus.org/quake3/](http://icculus.org/quake3/) ), are giving me assorted problems now. :( Seems like I'll have to resign to play WZ2100 on Windoze for now. 

Oh yes, also I tried to run the Windows version from WINE, and with no luck either.

---

### Post by Perfect Storm on 2006-07-27
Get a Nvidia card :KS ;)

---

### Post by shugie on 2006-07-27
Thanks for all the help. I tried the .debs but no love. I still get the audio problem from my second post. I have an nvidia card with driver installed. Sound works fine for everything else.

---

