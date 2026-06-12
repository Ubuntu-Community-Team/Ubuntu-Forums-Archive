---
title: "[SOLVED] firefox won't remember settings [Resolved]"
date: 2007-01-06
forum: Desktop Environments
---

### Post by liquid boy on 2007-01-06
in edgy, firefox has just started not remembering my settings (custom button layout) - i have had this problem in windows as well.

any ideas?

---

### Post by quartzy on 2007-01-06
```
cd ~/.mozilla/firefox/xxxxxxx.default
```

where xxxxxxx is just random numbers (it maybe different if you use profiles)

```
cp localstore.rdf localstore.rdf-backup
```

```
rm localstore.rdf
```

---

### Post by aysiu on 2007-01-06
You can also make you have ownership of the Firefox settings folder with this terminal command: ```
sudo chown -R liquidboy:liquidboy /home/liquidboy/.mozilla
``` Substitute in your real username for *liquidboy*.

---

### Post by liquid boy on 2007-01-07
thanks the first idea worked. 

cheers.

---

### Post by parrajeremy on 2008-06-03
Thanks aysiu. Your reply solved the problem for me on Hardy Heron using Firefox 3 rc1.

---

