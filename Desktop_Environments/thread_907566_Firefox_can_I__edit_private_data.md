---
title: "Firefox: can I  edit private data?"
date: 2008-09-01
forum: Desktop Environments
---

### Post by mringer on 2008-09-01
After using Firefox for a while, my private data acquires some junk:
e.g. I log into my mailserver and sometimes mis-spell my user name
and the mis-spelt names appear along with the correct name. I could
do  

tools > clear private data 

but would much prefer to edit it & delete only the junk. Please any
advice? Thank you.

---

### Post by p_quarles on 2008-09-01
My understanding is that Firefox uses SQlite tables to store this data, so it will be more complicated than simply editing a text file. The data is in:
```
~/.mozilla/firefox/XXXXX.default/
```

---

### Post by douglasbagnall on 2009-04-11
When the troublesome auto-complete item appears, select it with the arrow keys and press delete.

(based on a hint from: [http://labnol.blogspot.com/2006/03/firefox-search-bar-hacks.html](http://labnol.blogspot.com/2006/03/firefox-search-bar-hacks.html))

---

