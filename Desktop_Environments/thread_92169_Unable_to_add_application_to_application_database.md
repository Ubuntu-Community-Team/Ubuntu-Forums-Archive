---
title: "Unable to add application to application database"
date: 2005-11-18
forum: Desktop Environments
---

### Post by quonsar on 2005-11-18
i borked my desktop pretty badly fooling around with permissions (n00b!). i've got it mostly working again but i keep getting this message when i try to add, for example, gedit as a valid app for viewing a .css file. or any other app for other types of files. any clues? :smile:

---

### Post by mcduck on 2005-11-19
try to delete a directory called .local in your home directory. That is where all information about default applications lives, and if you have messed with it's rights that would cause exactly the same problems you're having.

Then logout and log back in and new .local is automaticly generated, and things should work again.

---

### Post by quonsar on 2005-11-19
thanks mcduck! that did the trick!

---

