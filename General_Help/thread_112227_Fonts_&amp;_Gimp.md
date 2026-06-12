---
title: "Fonts &amp; Gimp"
date: 2006-01-03
forum: General Help
---

### Post by NobleSavage on 2006-01-03
Can someone give me a quick run down on fonts? Or point me in the right direction. I did a search on the forum and didn't find what I need:

A friend gave me a bunch of TTF.  I'd like to import these and be able to use them with Gimp.  (Will they work system wide?)

Second, is there a program I can use to preview avaiable fonts?  I tried installing  gfontview and it didn't work. It said: can not open usr/x11R86/fonts/type 1  "File  Not Found".  Do I need to change something? Or is there a better program?

Thanks :D

---

### Post by matthew on 2006-01-03
Copy your font files (the .ttf's) to the hidden folder /.fonts in your home directory. They will then be available in Gimp, OpenOffice, and most other places as well.

/home/username/.fonts

As to the second question, I have no idea.

EDIT: To preview fonts I usually either open my word processing program or browse to the folder with the fonts using the file browser and just open them one by one. I am certain there's a better way--someone must have written a program for this, I've just never bothered to look for it.

---

### Post by NobleSavage on 2006-01-03
[QUOTE=matthew]Copy your font files (the .ttf's) to the hidden folder /.fonts in your home directory. They will then be available in Gimp, OpenOffice, and most other places as well.

/home/username/.fonts[/quote]

Well, I don't have a /.fonts in my home directory.  Do I just make it? Or do I have a problem because that folder is not there?


:confused:

---

### Post by matthew on 2006-01-03
Do this...from the main menu

Places->Home Folder

In the window that comes up,

View->Show Hidden Files

Then you should see a folder called .fonts that you can click to open. If it's not there then you can safely create one...but I would give very high odds it's there, just hidden.

---

### Post by NobleSavage on 2006-01-03
[QUOTE=matthew]Do this...from the main menu

Places->Home Folder

In the window that comes up,

View->Show Hidden Files

Then you should see a folder called .fonts that you can click to open. If it's not there then you can safely create one...but I would give very high odds it's there, just hidden.[/QUOTE]

Actually, I just did ~$ ls -a  and it didn't show up.  But there is a file called .fonts.cache-1  ?     I'll just make .fonts and see how that works.  Thanks!

---

### Post by NobleSavage on 2006-01-04
Matthew,

Hey, it's working perfect now. 1000 new fonts :p

---

### Post by matthew on 2006-01-04
[quote=NobleSavage]Matthew,

Hey, it's working perfect now. 1000 new fonts :p[/quote]Sweet. Glad to hear it. Have fun!!

---

### Post by cvmostert on 2006-01-05
i do not have a .fonts direcory, but i will try and make one to acchieve the same...

---

### Post by cvmostert on 2006-01-05
it worked! great...!!
thank you.

---

### Post by matthew on 2006-01-05
Cool. Glad it worked for you!

For those just joining us, if you don't have a /home/username/.fonts folder you can safely create one and put your ttf fonts in it.

---

