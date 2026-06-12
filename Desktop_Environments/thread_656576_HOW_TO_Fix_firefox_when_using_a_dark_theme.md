---
title: "HOW TO: Fix firefox when using a dark theme"
date: 2008-01-02
forum: Desktop Environments
---

### Post by rianquinn on 2008-01-02
open the following file:

sudo vim /usr/share/firefox/res/forms.css

and replace all:

```
background-color: -moz-Field;
```

and

```
color: -moz-FieldText;
```

with 

```
background-color: #ffffff; //-moz-Field;
```

and

```
color: #000000; //-moz-FieldText;
```

---

### Post by Trinexx on 2008-01-02
Nifty, although it only fixes the textinput areas. The main problem I have with FF under a dark theme is this...

---

### Post by heretic30117 on 2008-05-17
inside your firefox installation directory ( /usr/share/firefox/res/ )
```
sed -e 's/background\-color\:\ \-moz\-Field\;/background\-color\:\ \#ffffff\;/g' -e 's/color\:\ \-moz\-FieldText\;/color\:\ \#000000;/g' forms.css >>forms.css.new

mv forms.css forms.css.old&&mv forms.css.new forms.css

```

instead of searching through it all by hand.

---

