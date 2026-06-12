---
title: "Bibus - can't edit references or load styles after SPLite upgrade"
date: 2009-01-21
forum: Education &amp; Science
---

### Post by grw on 2009-01-21
Hi,

I have just installed bibus (version 1.4.3-2) on a new computer. I had to upgrade my database from sqlite2 to sqlite3 in order to open it (following instructions here: [http://www.sqlite.org/version3.html](http://www.sqlite.org/version3.html)). Everything appeared ok at first sight... 

But I can't open references to edit them (I can create new ones). All the info appears to be there when I click on teh 'details' tab, but nothing appears when I click on the 'styles' tab. The default style gives nothing either. And I can't seem to load styles, even ones I download from the styles repository.
 
Can anyone help?
Thanks
Gwyn

---

### Post by grw on 2009-01-24
Solved! I just exported everything as sqlite. Then ran the first connection wizard and everything works as it should. 
Gwyn

---

### Post by mdshaver on 2009-04-26
I think I'm having a similar problem. I had installed Jaunty after having created my Bibus database while using Intrepid. My old database with all my references is in SQLite2 but it seems that Bibus now needs to read SQLite3. I followed the link found in the above post but I am a newbie so I didnt have any luck converting my database to SQLite3. Any help would be greatly appreciated.

---

### Post by legatek on 2009-05-11
I'm having the same problem with the styles. I managed to convert my databases by using

```
sqlite OLD.DB .dump | sqlite3 NEW.DB

```

but I can't open any styles. I get the warning "The selected style is not a bibus style", even for software-bundled styles. Help!

---

