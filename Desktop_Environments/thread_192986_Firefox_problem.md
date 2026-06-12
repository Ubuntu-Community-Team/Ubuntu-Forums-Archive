---
title: "Firefox problem"
date: 2006-06-09
forum: Desktop Environments
---

### Post by PhilB on 2006-06-09
Have just installed the latest Firefox along with a number of other updates and I am having browsing problems. Basically I cannot get to any website using my bookmarks-the home page is ok and any links on it, also web pages in history can be accessed. 
Essentially the bookmark side bar is dead. All the bookmarks are ok in that the web address is correct and it looks as if I can copy and paste them into the address bar.
Phil

---

### Post by FredB on 2006-06-09
well... Close Firefox and launch terminal, and type :

```
cd .mozilla/firefox/
```

You should see a directory ending by .default.

Type ```
cd name-of-directory.default
```

In this directory, type "ls" (without ") and you should see 2 files ending by mfasl.

Type "rm -f *.mfasl" (without ")

And now, try removing localstore.rdf file using "rm -f localstore.rdf"

Close terminal and launch again firefox. It may work ;)

---

