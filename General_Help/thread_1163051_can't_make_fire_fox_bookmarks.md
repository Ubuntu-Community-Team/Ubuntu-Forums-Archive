---
title: "can't make fire fox bookmarks"
date: 2009-05-18
forum: General Help
---

### Post by ant2ne on 2009-05-18
I choose Bookmark this page and no bookmarks are made. I'm thinking permissions on whatever file/directory stores these bookmarks may be incorrect. Where can I find this file/directory? what would the permissions be?

---

### Post by sanderd17 on 2009-05-18
you can look in the directory below I suppose

```
~/.mozilla/firefox/rpnm8kre.Default/bookmarkbackups
```

just try to open in in nautilus (hit ctrl+h to show the mozilla folder) if you can not open it: it's indeed a simple problem with your permiissions.

---

### Post by michy99 on 2009-05-18
Bookmarks are stored in /home/{your-user-name}/.mozilla/firefox/q3cogte.default/bookmarks.html. It should be owned by you and you should have read and write permissions. Group and others should have read-only permissions.

Note that .mozilla is a hidden folder so you may have to press ctrl+h to see it. Also, the q3cogte may be different for you but it is probably the only folder in the firefox folder.

---

### Post by ajgreeny on 2009-05-18
> **michy99 said:**
> Bookmarks are stored in /home/{your-user-name}/.mozilla/firefox/q3cogte.default/bookmarks.html. It should be owned by you and you should have read and write permissions. Group and others should have read-only permissions.

Note that .mozilla is a hidden folder so you may have to press ctrl+h to see it. Also, the q3cogte may be different for you but it is probably the only folder in the firefox folder.
Assuming you are using Firefox 3.0.#, the bookmarks are now not in bookmarks.html but in places.sqlite.  You can still import the bookmarks.html if you wish but any changes you have made to them since using FF3 will not be saved there, only in the sqlite file (it's in the same folder as the html version).

---

### Post by michy99 on 2009-05-18
> **ajgreeny said:**
> Assuming you are using Firefox 3.0.#, the bookmarks are now not in bookmarks.html but in places.sqlite.  You can still import the bookmarks.html if you wish but any changes you have made to them since using FF3 will not be saved there, only in the sqlite file (it's in the same folder as the html version).

Thanks for the info. I guess my bookmarks.html file is leftover from FF2. The fact that it hasn't been modified since January might have been a clue :)

---

### Post by ant2ne on 2009-05-18
I chmod to 770. I still can not make new bookmarks.
```

ant2ne@2ne-buntu:~$ ls -l ~/.mozilla
total 8
drwxrwx--- 3 ant2ne ant2ne 4096 2008-05-08 17:44 extensions
drwxrwx--- 3 ant2ne ant2ne 4096 2008-03-15 16:22 firefox
```Any other advice?

---

