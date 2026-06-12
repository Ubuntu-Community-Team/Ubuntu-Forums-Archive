---
title: "quick vi question"
date: 2009-04-14
forum: General Help
---

### Post by fcuk112 on 2009-04-14
if i start to edit a file but then realise i needed to prefix it with sudo in order to save it down properly, is there a way from within vi to save the file down with sudo perms?

thanks.

---

### Post by Simian Man on 2009-04-14
Not as far as I know.  You can save it somewhere yo can write with:
```
:w ~/temp.txt
```

Then move it in place with:
```
sudo mv ~/temp.txt /file/you/meant/to/edit
```

---

### Post by Primefalcon on 2009-04-14
Simian is 100% correct...

---

### Post by fcuk112 on 2009-04-14
cool, thanks for the quick response!

---

### Post by fcuk112 on 2009-04-24
actually, just found out from stackoverflow.com that it is possible:

```

:w !sudo tee %

```

---

