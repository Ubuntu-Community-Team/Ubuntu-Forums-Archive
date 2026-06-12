---
title: "Unable rm directory with special character"
date: 2011-08-15
forum: Desktop Environments
---

### Post by Alistair George on 2011-08-15
Hi I have an upgrade to IGO maps and want to remove the old directory called "primo." and replace it with primo by first renaming primo. to primo then deleting it and contents. However unable to do first step of renaming the directory
Please see here:
```
alistair@alsmain /media/07DF-0002 $ ls -lN
ls: cannot access primo.: No such file or directory
total 368
-rw-r--r-- 1 alistair alistair 71700 2011-08-16 09:53 gpspara3.bin
-rw-r--r-- 1 alistair alistair    68 2011-08-15 15:56 NaviPath.txt
drwx------ 3 alistair alistair  8192 2009-01-01 01:00 Opera Mini 5
d????????? ? ?        ?            ?                ? primo.
```

Try command in term:
```
alistair@alsmain /media/07DF-0002 $ mv file:///media/07DF-0002/primo. primo
mv: cannot stat `file:///media/07DF-0002/primo.': No such file or directory
```


Any suggestions please?
Thanks,
Alistair.

---

### Post by nmaster on 2011-08-15
> **Alistair George said:**
> Hi I have an upgrade to IGO maps and want to remove the old directory called "primo." and replace it with primo by first renaming primo. to primo then deleting it and contents. However unable to do first step of renaming the directory
Please see here:
```
alistair@alsmain /media/07DF-0002 $ ls -lN
ls: cannot access primo.: No such file or directory
total 368
-rw-r--r-- 1 alistair alistair 71700 2011-08-16 09:53 gpspara3.bin
-rw-r--r-- 1 alistair alistair    68 2011-08-15 15:56 NaviPath.txt
drwx------ 3 alistair alistair  8192 2009-01-01 01:00 Opera Mini 5
d????????? ? ?        ?            ?                ? primo.
```

Try command in term:
```
alistair@alsmain /media/07DF-0002 $ mv file:///media/07DF-0002/primo. primo
mv: cannot stat `file:///media/07DF-0002/primo.': No such file or directory
```


Any suggestions please?
Thanks,
Alistair.

i don't think this has to do with the special character.  you don't have the appropriate permissions.

```
sudo chmod 777 /media/07DF-0002/primo.
```
then try running the command you want.

---

### Post by Alistair George on 2011-08-15
> **nmaster said:**
> i don't think this has to do with the special character.  you don't have the appropriate permissions.

```
sudo chmod 777 /media/07DF-0002/primo.
```
then try running the command you want.
Thanks but:
```
alistair@alsmain /media/07DF-0002 $ sudo chmod 777 /media/07DF-0002/primo.
[sudo] password for alistair: 
chmod: cannot access `/media/07DF-0002/primo.': No such file or directory

```
Even using  sudo chmod 777 "primo."

---

### Post by Bobhuber on 2011-08-15
> **Alistair George said:**
> Thanks but:
```
alistair@alsmain /media/07DF-0002 $ sudo chmod 777 /media/07DF-0002/primo.
[sudo] password for alistair: 
chmod: cannot access `/media/07DF-0002/primo.': No such file or directory

```Even using  sudo chmod 777 "primo."

You will have the same problem if you use spaces in directory names.
Enable the delete function in nautilus and open it as root (sudo nautilus)
You will then be able to rename or delete incorrectly named files or directories
I'm assuming 8.04 is a desktop version and has a nautilus. - I started with 9.04 so your a bit before my Ubuntu experience level.

---

### Post by Alistair George on 2011-08-15
> **Bobhuber said:**
> You will have the same problem if you use spaces in directory names.
Enable the delete function in nautilus and open it as root (sudo nautilus)
You will then be able to rename or delete incorrectly named files or directories
I'm assuming 8.04 is a desktop version and has a nautilus. - I started with 9.04 so your a bit before my Ubuntu experience level.

Sorry; remiss of me Nautilus does not show the primo. directory even when Ctrl-H (show hidden). Actually, that was the first method I'd tried. Welcome any other suggestions.

---

### Post by whatthefunk on 2011-08-15
Have you tried using the GUI?

---

### Post by Alistair George on 2011-08-15
> **whatthefunk said:**
> Have you tried using the GUI?
See previous - if you mean Nautilus.

---

### Post by whatthefunk on 2011-08-15
> **Alistair George said:**
> See previous - if you mean Nautilus.

*Slaps forehead* 
I should really read more carefully...

I dont think it has to do with the special character.  I just created a primo. directory in my home folder and was able to mv it and delete it with no problems.

---

### Post by fcomstoc on 2011-08-15
Have you tried to select it using tab completion (type the first few letters then press the tab key) this is the method i use to select files that have spaces in them

---

### Post by Alistair George on 2011-08-15
> **whatthefunk said:**
> *Slaps forehead* 
I should really read more carefully...

I dont think it has to do with the special character.  I just created a primo. directory in my home folder and was able to mv it and delete it with no problems.

No, I think it has to do with special character which is invisible eg the real dirname is different than primo.

I tried the same as you did earlier and a prepended or appended period doesnt affect the ability for nautilus to manage a directory.
I've also tried working on it with WinXP with similar results.
Cheers,
Al.

---

### Post by Alistair George on 2011-08-15
> **fcomstoc said:**
> Have you tried to select it using tab completion (type the first few letters then press the tab key) this is the method i use to select files that have spaces in them

Tab doesnt find it.

---

### Post by whatthefunk on 2011-08-15
Can your system find it with this?

```
locate primo
```

---

### Post by Alistair George on 2011-08-15
> **whatthefunk said:**
> Can your system find it with this?

```
locate primo
```

no

---

