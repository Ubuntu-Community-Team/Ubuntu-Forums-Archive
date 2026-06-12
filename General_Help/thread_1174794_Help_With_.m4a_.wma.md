---
title: "Help With .m4a/ .wma"
date: 2009-05-31
forum: General Help
---

### Post by kyle2595 on 2009-05-31
[SIZE=2]Hi, I have a big music[/SIZE][SIZE=2] library full of .m4a and .wma files, I was wondering if there was any way to play both of those file types in Banshee.  If not, is there a music player that will play both of those file types ( not Amarok)?  Thank you.[/SIZE]

---

### Post by jonathanysp on 2009-05-31
have you installed ubuntu-restricted-extras package? this has many codecs that are proprietory and is very useful

---

### Post by Bucky Ball on 2009-05-31
Adding the Mediabuntu repositories to your software sources will also help. Do a search for:

add medibuntu repository ubuntu

... and you should find plenty of help.

---

### Post by ActiveFrost on 2009-05-31
.wma belongs to restricted formats : [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by Soul-Sing on 2009-05-31
I think you need w32codecs installed for wma support, and faad for m4a support. Indeed restricted formats.

Banshee will play them allright.

---

### Post by kyle2595 on 2009-05-31
I have installed the ubuntu-restricted-extras package and followed the directions on [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5) and Banshee still does not play the .wma files.  the .wma files will play in Movie Player if i find the files in file browser, but they will not play in Banshee.

Edit - I think what I will do is try to convert my .wma files to .mp3 and see if that works.

---

### Post by Soul-Sing on 2009-05-31
> I think what I will do is try to convert my .wma files to .mp3 and see if that works.


Soundconverter does that job. (lame is already installed with the restricted package, i think?)

---

### Post by Bucky Ball on 2009-06-02
Once again, add the Medibuntu repository to your Software Sources. Go to this page and Item 4: Adding the Repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

