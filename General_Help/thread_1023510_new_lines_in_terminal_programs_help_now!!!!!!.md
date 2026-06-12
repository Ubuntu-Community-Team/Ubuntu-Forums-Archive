---
title: "new lines in terminal programs help now!!!!!!"
date: 2008-12-28
forum: General Help
---

### Post by SonnHalter on 2008-12-28
I NEED to know how to get a new line on terminal programs


like instead of:abcdefgh enter
i want: abcde
        fgh enter

---

### Post by shecky on 2008-12-28
Put a backslash at the end of the line.
```
echo abcde\
fgh
```

---

### Post by SonnHalter on 2008-12-28
didn't work. still just runs code. 
working on python right now. 

>>> print "hi" \ print "fgh"
SyntaxError: unexpected character after line continuation character
>>>

---

### Post by SonnHalter on 2008-12-28
didn't work. still just runs code. 
working on python right now. 

>>> print "hi" \ print "fgh"
SyntaxError: unexpected character after line continuation character
>>>

---

### Post by Ahadiel on 2008-12-28
> **SonnHalter said:**
> didn't work. still just runs code. 
working on python right now. 

>>> print "hi" \ print "fgh"
SyntaxError: unexpected character after line continuation character
>>>

I wouldn't use the python built-in interpreter for multiple lines of code.

---

### Post by shecky on 2008-12-28
Ah, you didn't specify python before.
```
>>> print "hi\nfgh"
hi
fgh
>>>
```

---

### Post by dagnabit dang doohickey on 2008-12-28
When entering a multi-line command, use a backslash and hit the Enter key after the backslash.
```
>>> print "Hello \<enter>
... World"

```
When entering multiple commands on one line, separate the commands with a semi-colon.
```
>>> print "Hello"; print "World"
```

---

