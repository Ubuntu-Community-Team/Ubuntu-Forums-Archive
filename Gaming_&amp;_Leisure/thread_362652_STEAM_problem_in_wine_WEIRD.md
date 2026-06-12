---
title: "STEAM problem in wine? WEIRD"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by ohmycar on 2007-02-15
I installed steam through wine and it installed and updated.
only when i open it up, it looks like this  

[IMG]http://img186.imageshack.us/img186/6572/untitlednz8.jpg[/IMG]

anyone know the cause or solution to this?

---

### Post by Motoxrdude on 2007-02-15
Not sure. probably just the fonts.
```
sudo aptitude install xfonts-intl-arabic
sudo aptitude install xfonts-intl-asian
sudo aptitude install xfonts-intl-chinese
sudo aptitude install xfonts-intl-chinese-big
sudo aptitude install xfonts-intl-european
sudo aptitude install xfonts-intl-japanese
sudo aptitude install xfonts-intl-japanese-big
sudo aptitude install xfonts-intl-phonetic
sudo aptitude install gsfonts-x11
sudo aptitude install msttcorefonts
sudo fc-cache -f -v

```

Are you able  to login though?

---

### Post by ohmycar on 2007-02-16
no i cant even type in the login fields. its weird.

edit: still didn't work after installing fonts. :(

---

### Post by Brynster on 2007-02-16
Its a font issue in the first instance

You need to search for tahoma:ttf fonts on google and down load and copy them over to the ./wine/windows/fonts folder

when you login to steam you'll then see the text. As far as entering you login details you need to right click in the text entry box to bring it into focus correctly to allow typing. (its a wierd glitch thats been around forever in Wine and the steam login system)

---

### Post by ohmycar on 2007-02-16
ah i see. 

thank you very much for all the help.
i love the ubuntu community. so glad i switched :)

---

### Post by ohmycar on 2007-02-18
well i downloaded the tahoma font. but when i go to put it in my wine folder. i do not see a .wine folder, even when i enable view hidden files.

is there anything i need to do prior to installing the fonts? like a wine config or anything?

thanks :)

edit: ok i see the folder now, but its a hidden folder and it is locked? how do i unlock it so i can move the font file into it?

---

### Post by ohmycar on 2007-02-18
ok well i used the sudo to move the fonts in the correct font folder, but now when i try to run the SteamInstall.exe with wine, i get this error message


[IMG]http://img504.imageshack.us/img504/7739/untitledlv0.jpg[/IMG]

---

### Post by Brynster on 2007-02-20
sorry i should have mentioned the .wine folder is a hidden file

On your desktop open Places>Home folder
on the tool bar View>Show hidden files

There should be then a lot of extra folders appear one should be .wine
from .wine its  .wine>Drive_c>Windows>Fonts

Put the tahoma:ttf file in there.

and hey presto that should sort it for you.

---

### Post by Bram77 on 2007-03-02
I'm having the exact same problem. I think it's related to the following error when updating the fonts-cache

```
/var/cache/fontconfig: cleaning cache directory
/var/cache/fontconfig: d8953eec0571530d8edc2100d26af76f-x86.cache-2: missing directory: /usr/share/fonts/X11/truetype
/var/cache/fontconfig: 8696880ae85222e874a1bbf1e643f1a6-x86.cache-2: missing directory: /usr/share/X11/fonts/truetype
/root/.fontconfig: not cleaning unwritable cache directory
```

I can create the truetype dirs manually, but as soon as I apt-get the ms core fonts the directory's are deleted again by the installation.


edit: I'm running Feisty Fawn Herd4 by the way.

---

### Post by Bram77 on 2007-03-02
I've solved the problem now by copying all the ttf fonts from my Windows Vista partition (I'm running a dualboot, although I haven't seen Vista for quite a while :)) to "/usr/share/fonts/truetype/msttcorefonts/"

---

