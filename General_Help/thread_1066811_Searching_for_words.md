---
title: "Searching for words"
date: 2009-02-11
forum: General Help
---

### Post by Simplemind169 on 2009-02-11
My class has just learned how to use grep and i am trying to complete on of the assignments. We have a file called 'LFComm' that we need to find all the words that start with b. the only way i know of is to use the command
```
grep [b] LFComm
```
this returns the lines that have that letter in it is there a way to get just the words themselves.
we may think it is a version issue i am currently running ubuntu 8.10

---

### Post by Dr Small on 2009-02-11
Try:
```
cat LFComm | grep b
```

---

### Post by Simplemind169 on 2009-02-11
that still displays the full line i need to display just the individual words

---

### Post by geirha on 2009-02-11
We can't do your homework for you. [http://www.regular-expressions.info/](http://www.regular-expressions.info/) is a great resource though, and always put the regular expression inside quotes ('')

Giving you a little hint here:
```
grep -o '\<b' LFComm
```

---

### Post by Simplemind169 on 2009-02-11
i wouldn't normally search on a forums if it was homework this is an inclass assignment the teacher told us to research if it is possible

---

### Post by geirha on 2009-02-11
Ok, in that case:
```

$ echo alpha beta gamma delta bword. abcde | grep -o '\<b[[:alnum:]_]*'
beta
bword

```

The \< matches start of a word (\> matches end of a word)
The b matches a literal b
[[:alnum:]_] matches any alphanumerical character and _. The * behind it means it should match 0 or more of that.

In the extended regular expression (used by egrep), [[:alnum:_] may be written \w (word) instead:
```

$ echo alpha beta gamma delta bword. abcde | egrep -o '\<b\w*'
beta
bword

```

Read grep's manual page
```
man grep
```

---

