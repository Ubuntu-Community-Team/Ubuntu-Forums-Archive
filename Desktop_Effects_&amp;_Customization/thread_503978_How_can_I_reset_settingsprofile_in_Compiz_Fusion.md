---
title: "How can I reset settings/profile in Compiz Fusion?"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by holihue on 2007-07-18
How can I reset all setting/profile in Compiz Fusion?

I tried to delete the .compizconfig and restarted compiz, but my settings was still there.

What is wrong?

I want to get the profile as it was at the start.


Thanks

---

### Post by holihue on 2007-07-18
I Used the system monitor on the CompizConfig Settings Manager, to check witch files the program used.

And it used /tmp/orbit-yourname/AFileIDon'tRemember

Then I deleted all files in the directory.

Thats it...



**WARNING!!! IF YOU DO THAT YOU LOSE A LOT OF SETTINGS LIKE THE WINDOW BORDER**

---

### Post by holihue on 2007-07-18
I had to move the files back because of nothing worked...


I need help!

---

### Post by Gen2ly on 2007-07-18
You could reset gconf but I'm not sure if there are stored there anymore:

[http://gentoo-wiki.com/Compiz#Resetting_gconf_Settings](http://gentoo-wiki.com/Compiz#Resetting_gconf_Settings)

You could manually start Compiz with the setting you'd like.  See if "compiz-start" is on your computer.

---

### Post by Gen2ly on 2007-07-20
I definitely realized this was for Compiz original, still I wish the post helped.

---

