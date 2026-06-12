---
title: "Can't get Windows TTF fonts working"
date: 2008-11-18
forum: Desktop Environments
---

### Post by keithld on 2008-11-18
I did get the core Windows fonts working but I have 2-CD's full of fonts that I used in Photoshop and Illustrator and I copied the most used ones about 50 or so to a hidden folder I created: home/.fonts and ran the cache command but none of those fonts show up in OpenOffice or any Gimp or any other program...

Any ideas guys????? 	](*,)


Thanks!!!

---

### Post by wylfing on 2008-11-18
1. What cache program did you run? I assume you mean fc-cache, but please specify exactly what you typed.

2. Check the permissions and ownership of the files in your ~/.fonts directory. They should all be owned by you (and probably your group as well). The permissions should be 755 (-rwxr-xr-x).

---

### Post by keithld on 2008-11-18
this is the command I ran for the cache: $sudo fc-cache -fv

All files are owned by Administrator & Groups.

---

### Post by anaranjado on 2008-11-18
Create a dir in /usr/share/fonts/:
[COLOR="RoyalBlue"]cd /usr/share/fonts/[/COLOR]
[COLOR="RoyalBlue"]sudo mkdir win_fonts[/COLOR]

Copy your fonts into this dir:
[COLOR="RoyalBlue"]cd win_fonts[/COLOR]
[COLOR="RoyalBlue"]sudo cp ~/xxxx/* .
[/COLOR]
And then:
[COLOR="RoyalBlue"]sudo chmod 644 *[/COLOR]
[COLOR="RoyalBlue"]sudo mkfontdir[/COLOR]
[COLOR="RoyalBlue"]sudo mkfontscale[/COLOR]
[COLOR="RoyalBlue"]sudo fc-cache[/COLOR]

---

### Post by keithld on 2008-11-18
Got the fonts copied anaranjado, but I noticed it didn't copy all of them I had in ~/.fonts

I checked OpenOffice again and the ones that it did copy are showing up but fonts like Tiffany & the rest did not copy nor do they show up In Open Office  they do show up in Nautilus when I look at the .fonts folder and all their permissions are set to Administrator...

Is there a limit to how many fonts can be installed and loaded in Linux?

---

### Post by anaranjado on 2008-11-18
I have only installed dozens of windows fonts, so I don't know if there is a limit.

make sure the names of the font files don't contain special characters and ........ you have enough disk space on your / partition. 

......... -_-!!

---

### Post by Frogbarf on 2008-12-02
> **keithld said:**
> this is the command I ran for the cache: $sudo fc-cache -fv

All files are owned by Administrator & Groups.

Maybe I'm revealing my ignorance, but I use **sudo fc-cache -f -v**

---

### Post by Zorael on 2008-12-03
> **Frogbarf said:**
> Maybe I'm revealing my ignorance, but I use **sudo fc-cache -f -v**
Syntactic sugar, both syntaxes work. :3

---

### Post by keithld on 2008-12-03
Got 'em working, thanks guys...

---

