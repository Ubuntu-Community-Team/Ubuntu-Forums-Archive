---
title: "Font Issues - Display Problems"
date: 2011-06-09
forum: Desktop Environments
---

### Post by ChrisNZ on 2011-06-09
Hi all

Currently I'm running Ubu Natty and it's been fairly good so far, however one small issue. Fonts displayed (Times Romans in particular) in some programs display the capitals as a variant/architectural or a non traditional display? 
I have uploaded several fonts from a net based supplier and wondering this has caused a conflict somewhere?

Can someone help with finding out what could be causing this problem please.

I'll try to upload a picture?

Keywords - Fonts Display Issues Natty

---

### Post by 23dornot23d on 2011-06-09
Type 

font-manager

in a terminal ...... see what it gives you for Times Roman mine is like this ,,

[IMG]http://img806.imageshack.us/img806/8740/fonts1.jpg[/IMG]


Does it display properly in there ...... if not it may need to be put back ..... or maybe another one used ....

Interesting Link too ...... [LINK]("http://www.linuxlibertine.org/index.php?id=91&L=1")

---

### Post by ChrisNZ on 2011-06-09
Found out that Font-Manager was not loaded as part of Natty. Loaded now.

Times New Romans not found on the system, neither is Ariel? Now this is of course looking at a document in Libra Office Writer? I can type in Libra writer the font in the font box and it will change to Ariel with no apparent problem, its just not listed in the drop box?? 
Surely the font manager would of found all fonts? Very strange then that it will format a display for Times Romans and Ariel but not in upper case on Times Roman??

---

### Post by 23dornot23d on 2011-06-09
I do not know if it makes any difference but 
I also add fontforge too and fontforge-extras

I do not use the office tools much only Gimp and add the fonts
in there ...... as a separate option.

Maybe Libre Office is similar ..... for adding fonts to it ..... maybe they need to
be individually picked or maybe a folder.

But I would have expected System/Global Fonts are automatically picked up by it .....

Hope some one else sees this and has a solution for you ....

---

### Post by ChrisNZ on 2011-06-11
Yes - I know the program you mean.

Q: Is this issue also reflected in things like PDF files? For example i downloaded a few recently and noticed the same font issue as above. But not on all of them. So i'm thinking that the pdf files used a mixture of the ms Times Romans and something else which was a font loaded already or avail to Libra Writer?

I also gave LW the options of changing any document that has Times Romans to the new Liberation Serif fonts i loaded.

Cheers
Chris

---

### Post by 23dornot23d on 2011-06-11
When you say this ... in the first thread ..... do you have a link to where you got them from.

> 
I have uploaded several fonts from a net based supplier and wondering this has caused a conflict somewhere?
They may have overwritten the main ones ..... but I would like to see how 
they download and how they install ......  the ones you got to work .....

---

### Post by ChrisNZ on 2011-06-18
Hi 23dornot23d

I have got them from 

[http://www.fontspace.com](http://www.fontspace.com) 

if that helps and have not wanted to get 'another' times roman' font so unsure how an existing font was or could have been, overwritten by a 'different name' font? 

I now only find that only some pdf files when opened show this weird font, not all!?

cheers

---

### Post by Rod J on 2011-06-18
Hi ChrisNZ,

I'm running 10.04 Lucid so I don't know if Natty is still the same. 

This might help: sudo fc-cache -fv (resets the font cache after deleting/adding fonts). Also, I think the best way to get the MS core fonts (including Times New Roman) is to install the package ttf-mscorefonts-installer (Installer for Microsoft TrueType core fonts).
 
When manually adding fonts I usually put them into the /usr/share/fonts location so they are available system-wide.

---

### Post by ChrisNZ on 2011-06-18
Hi Rod J

I checked the ttf-mscorefonts-installer and it's loaded already so that should have helped the font issue too.

_The Process I use._
When I upload fonts I put them into a folder under "home<New Fonts". Most are a zip file, so it opens the archive manager and i extract them into a sub folder of 'New Fonts' simply called "fonts". Then I select the new font, open font viewer and see the "install font" button - if it has not been installed and make that happen. Then delete the zip file. 
So by doing this am i preventing the system seeing all fonts correctly and thereby it only sees fonts "selectively"?? This may mean i have to move them to the user/share/font folder then?

Cheers

---

### Post by Rod J on 2011-06-19
I think installing the fonts the way you are doing should be OK, especially using the font viewer to install them (although when I use the font viewer here the button on the bottom still says "install" even though the fonts are installed ... not sure why that is?). Maybe you could try this to make sure the font directory is found:

sudo fc-cache -fv ~/New\ Fonts/{dir}

It's certainly a strange problem you are having, can't say I've ever seen fonts behaving that way. It seems to me like the Times New Roman font file is damaged in some way or perhaps some conflict with two versions of the font installed at the same time in different locations?

---

