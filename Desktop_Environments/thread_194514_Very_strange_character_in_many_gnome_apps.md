---
title: "Very strange character in many gnome apps"
date: 2006-06-11
forum: Desktop Environments
---

### Post by ilans on 2006-06-11
Attached screenshot:
[http://www.sendit.co.il/pics/upservl/3a542ce155.png]("http://www.sendit.co.il/pics/upservl/3a542ce155.png")

This strange character accour in:
gedit, gnome baker, mysql-query-browser and many many more apps :(  

locale definition::
ilan@ilan-Ubuntu:~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en_GB:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by Choad on 2006-06-11
that character is used when the current font being used doesnt have a character for the character that is supposed to be there.

go to a chinese site and the browser will fill up with them

so.... not sure how u'd fix it. search for some kind of extended character set font thingg

---

### Post by sarhento_lobo on 2006-06-11
Right, those characters mean that they can't be read by your current encoding, which is utf-8; that is, there isn't an equivalent for them. You can try changing your encoding if you want lots of characters to be readable (unicode might be worth a shot).

---

### Post by Turin Turambar on 2006-06-17
I have the same problem. How can I change from UTF-8 to unicode?

---

