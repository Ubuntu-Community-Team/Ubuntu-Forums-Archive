---
title: "Language translator"
date: 2008-03-06
forum: Education &amp; Science
---

### Post by L815 on 2008-03-06
What is the best language translator program?

Things I need:
-Accurate as possible
-Wide range of languages (mainly korean, japanese, french, portuguese)
-Able to translate text fairly accurately 
-Easy to use


Thanks :)

---

### Post by Festor on 2008-06-10
gnome-translate ¿?

---

### Post by Amilo1718 on 2009-07-21
Can someone recommend a program with hungarian language (from/to) ?

gnome-translate doesn't have the hungarian language...

Many thanks

---

### Post by sisco311 on 2009-07-21
> **Amilo1718 said:**
> Can someone recommend a program with hungarian language (from/to) ?

gnome-translate doesn't have the hungarian language...

Many thanks

Edit the /usr/share/libtranslate/services.xml file:
```
gksu gedit /usr/share/libtranslate/services.xml
```
and add the bold line to the google section:
```
...
  <service nick="Google" name="google">
    <group>
      <language to="*" tag="en"/>
      **<language to="en" tag="hu"/>**
      <language to="en" tag="ar"/>
      <language to="en,fr" tag="de"/>
      <language to="en" tag="el"/>
      <language to="en" tag="es"/>
      <language to="en,de" tag="fr"/>
      <language to="en" tag="it"/>
...
```

(re)start gnome-translate.

```
echo "Hope this helps. Good luck." | translate-bin -s google -f en -t hu
Remél ez segít. Sok szerencsét. <br>                                           

```

Nem tökéletes de azért elmegy. :)
(It's not perfect but it works.)

---

### Post by Amilo1718 on 2009-07-21
Many thanks

---

