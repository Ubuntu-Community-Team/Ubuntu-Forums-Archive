---
title: "new bash command creation problem"
date: 2009-05-24
forum: General Help
---

### Post by netimen on 2009-05-24
I have created a command wich is convenient for me:
```
lcd() { cd ${1} ; ls ; }
```
but when I type
```
lcd Tom\ &\ Jerry
```
where Tom & Jerry is an existing folder, I get
```
bash: cd: Tom: No such file or directory
```
How to fix this?

---

### Post by kmitnick on 2009-05-24
try 
lcd 'Tom & Jerry'

---

### Post by netimen on 2009-05-24
> **kmitnick said:**
> try 
lcd 'Tom & Jerry'

Thanks, but that didn't help

---

### Post by kmitnick on 2009-05-24
where are you trying to add the lcd function???

---

### Post by netimen on 2009-05-24
> **kmitnick said:**
> where are you trying to add the lcd function???

I added it to the .bashrc and it works OK if a folder name doesn't contain spaces

---

### Post by kmitnick on 2009-05-24
neither the ' nor " worked try
"Tom & Jerry"

---

### Post by netimen on 2009-05-24
> **kmitnick said:**
> neither the ' nor " worked try
"Tom & Jerry"

still the same effect

---

### Post by kmitnick on 2009-05-24
I made this```

lcd(){
echo "Accessing "${1};
cd "${1}";
ls;
}

```
this should work with you and when you run lcd
use as I told you 
```
lcd "Tom & Jerry"
```

---

### Post by netimen on 2009-05-24
> **kmitnick said:**
> I made this```

lcd(){
echo "Accessing "${1};
cd "${1}";
ls;
}

```
this should work with you and when you run lcd
use as I told you 
```
lcd "Tom & Jerry"
```

Thank you! this works even if I without quotes ```
lcd Tom & Jerry
```

---

### Post by kmitnick on 2009-05-24
another satisfied customer :D
glad to hear that

---

### Post by kmitnick on 2009-05-24
mark it as solved please

---

### Post by netimen on 2009-05-24
> **kmitnick said:**
> mark it as solved please

If I understood well, that feature has been removed: [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by kmitnick on 2009-05-24
aha I am new to UbuntuForums i am a user at Linuxforums and it is an available feature in that forums

---

