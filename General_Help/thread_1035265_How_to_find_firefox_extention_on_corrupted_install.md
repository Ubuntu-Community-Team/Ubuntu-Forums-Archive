---
title: "How to find firefox extention on corrupted install"
date: 2009-01-09
forum: General Help
---

### Post by mylifedrive on 2009-01-09
I installed an extention onto firefox in Ubuntu linux running off a flash drive. Now I get kernel panic errors, (not caused by the extention) and I would like to install the same one on my new install. 

The extention was an Rss reader that would combine the feeds and tell how many unread posts you had, etc. I can't find it again.

Well, now I am on a new install, and I put in the old flash drive, where should I navigate to to find the add-on? (If I find out the name, then I can find it again on the web)

---

### Post by anystupidname on 2009-01-09
If I had to guess which extension it was, I'd say Sage?
But, to answer your question, if you look in this file (with nano for example) for each {<blah>} folder, you should find what you're looking for.
/home/<your username>/.mozilla/firefox/<random>.default/extensions/{<blah>}/install.rdf
(in rare cases <blah> might actually even say the extension name)

---

### Post by ibuclaw on 2009-01-09
Should be in this folder:
```
/home/**uname**/.mozilla/firefox/*.default/
```
You should find the name somewhere after a brief look around.

[EDIT]
A quick script printed a list of the extensions pulled from the prefs.js file in the folder:
Just cd to the directory above in your flash drive.
```
sed '/exten/!d;s/,\|:/\n/g;s/ \|\"//g' prefs.js | sed '/@/!d;s/^\(.*\)\@.*$/\1/'
```

Regards
Iain

---

