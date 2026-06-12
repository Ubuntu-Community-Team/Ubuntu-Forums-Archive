---
title: "when i access files from terminal they show up blank??"
date: 2009-05-31
forum: General Help
---

### Post by Shpongle on 2009-05-31
any idea why this is happening? or how i could fix it, like the file are there if i manually go to the directory and open them but when i do it from terminal they come up blank!

---

### Post by mcduck on 2009-05-31
> **DillByrne said:**
> any idea why this is happening? or how i could fix it, like the file are there if i manually go to the directory and open them but when i do it from terminal they come up blank!

Make sure you type the file name (and path ) correctly.

If you try to edit a file that doesn't exist most editors will create empty file with the name you used.

---

### Post by Shpongle on 2009-05-31
i do type the path correctly, and the file already exists , like when i was editing the alsa-base file it opened blank , despite me having just opened it manually and seen all the data!

---

### Post by whoop on 2009-05-31
> **DillByrne said:**
> i do type the path correctly, and the file already exists , like when i was editing the alsa-base file it opened blank , despite me having just opened it manually and seen all the data!

what command(s) are you using. Try opening them with sudo.. Or it could be that the files are hidden, ls -A ?

---

### Post by Shpongle on 2009-05-31
for example id use sudo gedit /ect/modprobe.d/alsa-base
 no the files aren't hidden

---

### Post by Shpongle on 2009-05-31
heres a screen of it

---

### Post by mcduck on 2009-05-31
> **DillByrne said:**
> for example id use sudo gedit /ect/modprobe.d/alsa-base
 no the files aren't hidden

that would be "gksudo gedit /**etc**/modprobe.d/alsa-base**.conf**".. ;)

---

### Post by _Purple_ on 2009-05-31
> **DillByrne said:**
> for example id use sudo gedit /ect/modprobe.d/alsa-base
 no the files aren't hidden

```
gksudo gedit /etc/modprobe.d/alsa-base 
```

You typed 'ect' instead of 'etc' and please use gksudo instead of sudo while using gui based application.




edit: mcduck was faster :P

---

### Post by Shpongle on 2009-05-31
thanks man , that was it!, i thought i had botched it up in some way!,

---

### Post by mcduck on 2009-05-31
Great way to avoid that kind of problems (and also make working with files in terminal easier) is to use tab-autocompletion.

For example to type that path you'd type something like this:

"gksudo gedit /e<TAB>modp<TAB>a<TAB>"

Every time you press <TAB> the path will be completed if the part you have typed only has one possible match. (if there are many possible matches you can press <TAB> again to see a list of them, or type some more letters and try autocompleting again.

---

### Post by Shpongle on 2009-05-31
cool thanks for the help and the tip! :)

---

