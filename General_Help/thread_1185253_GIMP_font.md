---
title: "GIMP font"
date: 2009-06-12
forum: General Help
---

### Post by Utsukushii Tsubasa on 2009-06-12
im not really sure where this should go so yea. but in the font on "GIMP" they give you previews of the font. but when i try to use one of them, it just looks the same as normal. im pretty sure you understand my question by now. why does it look normal. another question is if i download a font from the net, where do i save it so it will show up in gimp?
Thanks in advance,
Utsukushii Tsubasa

---

### Post by hal8000 on 2009-06-12
When you look at the list of fonts, the "text description" is the same font but when you actually use and place text into an image, you will see the differenece between font styles.

Fonts are stored in

/usr/share/fonts


Use synaptic and install ttf-mscorefonts-installer if you want microsoft softs or any of the other great looking linux fonts available through synaptic.

For more help on gimp:
[http://docs.gimp.org/2.6/en/gimp-using-fonts.html](http://docs.gimp.org/2.6/en/gimp-using-fonts.html)

---

### Post by ad_267 on 2009-06-12
You can also put fonts in ~/.fonts. That means the fonts will only be available for your user, but you don't need administrative privileges to add new fonts.

---

### Post by Utsukushii Tsubasa on 2009-06-12
well i understand the word description, but all when i do that, the fonts still look the same. even when i test them. and since its my computer for one, shouldn't i have administrative acces??
i go to unpack a file, and it says "You don't have the right permissions to extract archives in the folder"
word for word.

---

### Post by Chronon on 2009-06-12
You need to run the archiver as root to extract to that directory.  It's better to temporarily become root to edit the directory than to change the permissions so that your (single) user account can edit it directly.

---

### Post by Utsukushii Tsubasa on 2009-06-12
how the heck do i do that?
yea, i know, i be a noob

---

### Post by ad_267 on 2009-06-12
> **Utsukushii Tsubasa said:**
> how the heck do i do that?
yea, i know, i be a noob

You can just put them in ~/.fonts like I said, or press Alt+F2 and run "gksu nautilus", then enter your password.

---

### Post by Utsukushii Tsubasa on 2009-06-12
i tried your first option, and that didnt work do to it didnt show in GIMP.
ill try the second option, but im not sure how that will work (no idea what that does)

---

### Post by Utsukushii Tsubasa on 2009-06-12
okie dokies second one worked i think.
thank you guys again ^^
now to watch movies :popcorn:
WTF??:p

---

### Post by ad_267 on 2009-06-12
... Do you want to play a DVD? [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Utsukushii Tsubasa on 2009-06-12
no i was making a joke about how i spent all this time trying to figure out how to get the fonts and things to go all to end up watching a movie.

---

### Post by ad_267 on 2009-06-12
Ah ok never mind then :)

---

