---
title: "openoffice 2, num pad dot to do comma in Calc"
date: 2005-10-26
forum: Desktop Environments
---

### Post by IdoMcFly on 2005-10-26
Hello, 

With openoffice 1, there was a macro to add to get the dot key of the num pad to do a comma in Calc for French people (we use comma instead of dot to separate the decimals).

It was said the problem is corrected in OpenOffice 2 but I can't get it work. My language options are set to french, the checkbox for the decimalk separator is checked, and the num pad dot key still give me a dot instead of comma.

Any help appreciate.

---

### Post by IdoMcFly on 2005-10-27
any clue?

---

### Post by IdoMcFly on 2005-10-28
:-/

---

### Post by foxy123 on 2005-10-28
I would advise you to ask at Ooo forum, they are more competent in Ooo specific stuff...

---

### Post by IdoMcFly on 2005-10-28
create a script:

```
#!/bin/sh
val=`xmodmap -pke | grep "keycode  91 = KP_Delete KP_Decimal"`
echo $val
if [ -n "$val" ]
then
        xmodmap -e 'keycode 91 = KP_Delete comma'
else
        xmodmap -e 'keycode 91 = KP_Delete KP_Decimal'
fi
```

make it executable

launch it in the session and the numpad dot will do a comma in OOo2 (Calc, Writer...)

---

### Post by kustodian on 2008-05-08
> **IdoMcFly said:**
> Hello, 

With openoffice 1, there was a macro to add to get the dot key of the num pad to do a comma in Calc for French people (we use comma instead of dot to separate the decimals).

It was said the problem is corrected in OpenOffice 2 but I can't get it work. My language options are set to french, the checkbox for the decimalk separator is checked, and the num pad dot key still give me a dot instead of comma.

Any help appreciate.
I know that this was asked about 3 years ago, but I had this same problem, and here is a  very simple solution:

open Openoffice.org->Tools->Options->"Language Settings"->Languages and set you language in "Locale Setting" and enable "Decimal seperator key" "Same as locale setting".

---

