---
title: "Where are my firefox bookmarks located?"
date: 2009-03-17
forum: General Help
---

### Post by whoop on 2009-03-17
I have got a modest amount of bookmarks under the Bookmarks file menu in firefox. I would like to know where these bookmarks are physically stored.
I have read in various posts that it should be under something like:
/home/user/.mozilla/xxxxxxx.default/bookmarks.html

When I check this file it just contains some default bookmarks like "getting started" "about us" etc. None of my custom bookmarks are in this file.

Where could my bookmarks be located?

---

### Post by lvleph on 2009-03-17
It should be something like
/home/<user>/.mozilla/firefox/xxxxxxxx.<user>/bookmarks.html

The user could be default or your user name.

---

### Post by fcuk112 on 2009-03-17
have you looked under ~/.mozilla/firefox/xxxxx.default/bookmarkbackups/ ?
on a side node, you should check out **delicious**.  a much better way to store bookmarks imho.

---

### Post by gheeke on 2009-03-17
Firefox3 uses an SQLLite Database for storing the bookmarks instead of the bookmarks.html file. All your bookmarks are now in the file places.sqlite. It's a binary file. Firefox makes backups of this file. You can find them in the folder bookmarkbackups. Those are - more or less - readable. In case you lose your database or it gets corrupted, you can import these files through Bookmarks –> Organize Bookmarks –> Import and Backup –> Import.

---

### Post by lvleph on 2009-03-17
So then the bookmarks.html file is just left over then?

---

### Post by ene_dene on 2009-03-17
I'm not sure if this is what you want, but you can easily export the bookmarks, by going to bookmarks->organize bookmarks->import and backup->export bookmarks. And then bookmarks will be saved in html file.
Hope this helps.

---

### Post by gheeke on 2009-03-18
> **lvleph said:**
> So then the bookmarks.html file is just left over then?

More or less...it's used for initially generating the database.

However you can configure FF to automatically export your bookmarks from places.sqlite to bookmarks.html. To do this, type about:config in the FF3 address bar. Klick OK.  Search for browser.bookmarks.autoExportHTML. The default value is false. Change it to true. Now new bookmarks will be saved into places.sqlite and bookmarks.html. Keywords and Tags however, will only be saved into the database.

---

