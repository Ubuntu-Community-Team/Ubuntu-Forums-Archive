---
title: "openoffice problem"
date: 2009-02-21
forum: General Help
---

### Post by arvsr1988 on 2009-02-21
hey whenever ive been hitting ctrl+s while using open office it just closes down. the same happens when i click save or save as. anyone know how to fix this bug?

---

### Post by prinny42 on 2009-02-21
I'm not sure if I'll be able to help, as I'm not all that experienced myself, but others will probably be better able to help you if you do this.

Please, first of all, specify what Open Office application you're using (Writer, Impress, Calc, etc).

Also, please post any errors the program gives; you can collect them in a text file in your home directory with this command:

```
oowriter 2> ~/errors.txt
```

Simply reproduce the crash once the program opens.  Also note than I have assumed you were using Writer.  If that is not the case, simply replace "oowriter" with the appropriate command (for instance, "oocalc"), which can be found in the manual, which you can find by issuing this command:

```
man ooffice
```

---

