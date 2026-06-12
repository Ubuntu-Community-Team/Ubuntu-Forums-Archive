---
title: "this is becoming annoying"
date: 2006-04-17
forum: Desktop Environments
---

### Post by runefreak on 2006-04-17
i have tried everything i can not get jre to install what should i do?
](*,)

---

### Post by K.Mandla on 2006-04-17
The instructions here

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

have worked perfectly for me each time. What method are you using?

---

### Post by runefreak on 2006-04-17
Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type: what does this mean?
](*,)

---

### Post by Omnios on 2006-04-17
Try Automatrix unless you raely want to figure out how to install it from source. Basicly automates a lot of the install stuff automatically inclduing java.

[http://ubuntuforums.org/showthread.php?t=80295]("http://ubuntuforums.org/showthread.php?t=80295")

---

### Post by K.Mandla on 2006-04-17
[QUOTE=runefreak]Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type: what does this mean?
](*,)[/QUOTE]
If I understand you correctly, it means you need to open the terminal and change to the directory where you downloaded the Sun Java package. 

Chances are when you downloaded it, it went into your home directory, so it should be right there when you open a terminal. Try this: Click on Applications > Accessories > Terminal. Then type:

```
ls
```
You should see the Java package right there. If not, use the **cd** command to change to the directory where you downloaded it.

---

