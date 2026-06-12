---
title: "How do you cd into this"
date: 2006-01-05
forum: Desktop Environments
---

### Post by UnknownPg on 2006-01-05
ok im trying to cd through console into the folder named "My Documents" and i cant seem to do it. any help?

---

### Post by rjwood on 2006-01-05
first off, where is your "my documents" folder?

---

### Post by UnknownPg on 2006-01-05
its in my media/sda1/Documents and Settings/<name>/My Documents
i know how to get into the Documents and Settings by cd Docume~1 but how to i get into My Documents

---

### Post by Omnios on 2006-01-05
[QUOTE=UnknownPg]ok im trying to cd through console into the folder named "My Documents" and i cant seem to do it. any help?[/QUOTE]

You can do somethine like this
```
 tom@main:~$ cd /home/tom/'My Downloads'
```

 Or think my term may be acting funky but
```
tom@main:~$ cd 'My Downloads'
```

 basicly wrap the multi word filename with '.....' but thought it had to be /'My Downloads' ??

---

### Post by UnknownPg on 2006-01-05
thankyou omnios that worked perfectly

---

### Post by redactech on 2006-01-05
You can also try the autocomplete feature


for example the /home/vladimir/documents/My documents exist

if you type cd /home/vladimir/documents/My then press tab documents should appear with the escape character

---

### Post by leech on 2006-01-05
Yeah, it could also be /media/sda1/My\ Documents/

Leech

---

