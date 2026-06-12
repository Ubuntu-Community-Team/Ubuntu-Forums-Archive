---
title: "Certain fonts don't work...ttf"
date: 2008-12-03
forum: General Help
---

### Post by notesetter on 2008-12-03
I'm having what I think is an unusual experience. I have a truetype font installed on my system that used to work with OOo 2.4. Since I upgraded to OOo 3.0, the font no longer works. I can select it from the list of available fonts, but the text characters don't change in my document.

The font is called EngraverTextT and it is a special music character face intended to be mixed with regular text faces.

UbuntuStudio 8.04

Anyone want to take a peak?

Thanks,

David

---

### Post by sanus|art on 2008-12-03
Have you tried to refresh the fonts catche:
```
fc-cache -fv
```

---

### Post by notesetter on 2008-12-03
Hello.

I have tried a few things. I copied the font file from my home/.fonts directory and into /usr/share/fonts/truetype and then refreshed the cache. Afterward, no go. So I rebooted and tried again...still not working.

I'm going to completely remove the ttf from my system in all fonts folders, refresh the cache, then put a clean copy back in /usr/share/fonts/truetype and try again. I'll post back tomorrow with the steps I've taken and the results.

It worked before the update to 3.0. The only difference I can think of is that OOo 2.4 was from the Ubuntu repositories and the new version was installed via the .deb package from the OOo website. That shouldn't make a difference, unless it's a bug of sorts. There are two other similar symbol fonts that don't display either. Might it be some problem with encoding (i.e. UTF-8 vs. ASCII)? I don't even know what I would have to change or how to do it if that's the case.

---

### Post by notesetter on 2008-12-04
I've completely removed all instances of the ttf in question and run ```
sudo fc-cache -f -v
```. I then copied the ttf from its original source into /usr/share/fonts/truetype. Afterwards, I could see the font in the OOo list, but selecting it didn't change characters in a document to that font. Running ```
sudo fc-cache -f -v 
``` again didn't solve the problem. I've successfully used other fonts that I've installed in this way just this morning, so, I don't know why this particular ttf is not being accessed by OOo. The character map program doesn't display the glyphs in the ttf file either. Strange.

I used to be able to use this font on this machine with this version of Ubuntu Studio. Could this be a Pango problem?

Dave

---

### Post by sanus|art on 2008-12-04
If your font is in /home/$USER/.fonts/ you should not run font cache refresh as super user (do not use 'sudo', as it trying to reCache fonts in /root).
The following page contains some font names with their representation, scroll to "E" and see if the "EngraverTextT"  displayed as it supposed to be. (If not - it is a system-wide problem - not OOO's).

PAGE: [http://www.gshoemaker.net/FPFontTables.htm](http://www.gshoemaker.net/FPFontTables.htm)

P.S. I've installed OOO3 too, where can  find the "EngraverTextT" font for download? Is it free/freely available? I want to test it on my laptop.

---

### Post by notesetter on 2008-12-04
I install fonts in /usr/share/fonts because I want to make them available to all accounts on the computer. Does ```
sudo fc-cache -f -v
``` refresh the system-wide font cache?

BTW, EngraverTextT is on the page you linked to and it displays correctly on that page, so I guess it's not a system problem.

EngraverTextT is licensed by Coda Music Technologies and is not freely available.

I'll try the Gimp and some other programs with it to see if it's an OOo 3.0 problem.

Thanks,

Dave

---

### Post by notesetter on 2008-12-04
The Gimp and Inkscape both render this font without any problems.

---

### Post by sanus|art on 2008-12-05
Try reading the following page than, it explains how to install fonts for open office exclusively:
[http://wiki.services.openoffice.org/wiki/Font-FAQ#How_do_I_add_fonts_to_OpenOffice.org_2_exclusively](http://wiki.services.openoffice.org/wiki/Font-FAQ#How_do_I_add_fonts_to_OpenOffice.org_2_exclusively)

---

### Post by notesetter on 2008-12-05
Thanks again.

In 8.04 with OOo 3.0 installed, the closest analogue I see for the OOo fonts dir is /opt/openoffice.org3/basis-link/share/fonts/truetype.

Installing the font in that folder didn't change the behavior of OOo 3.0 when I select that font. That page you linked to gave me some other ideas though. I'm going to research it a bit from the OOo wiki and see what I come up with.

Dave

---

### Post by Kellemora on 2008-12-05
Hi Notesetter

I checked to see if I had a copy of that font in stock but I don't, sorry.

We loose about 2% of our font base per year, they just self-corrupt for some reason and need to be reloaded from the original files.  2% don't sound like much until one realizes that means we have to restore roughly 5,000 font's per year.

If you still have the original install CD from when you loaded the program originally, perhaps you can try a new copy of the font from that.

Some special proprietary fonts designed for writing sheet music may not work in a standard text editor, due to the height of the font itself.  I had a program eons ago called Composer and the fonts from it would sometimes work in msWord and sometimes not, depended upon a line height setting or kerning if I remember right.  Although it was considered a ttf font, I think in reality it was really a rasterized font stored as ttf.

But I think perhaps the font may have become corrupt and just needs reloaded from the original source, not from a backup which could be corrupt.

Good Luck

TTUL
Gary

---

### Post by notesetter on 2008-12-05
Gary,

If I do insert=>special character and choose EngraverTextT from the font list, I can then insert the character I want to use. I don't think the font file is corrupt, I think it has to do with some change in the way OOo handles some symbol fonts between 2.4 and 3.0. It's the same with one or two other special symbol fonts. I could use them like any other font in OOo 2.4, but to access the glyphs in OOo 3.0, I have to insert them as special characters.


Regards,

Dave

---

