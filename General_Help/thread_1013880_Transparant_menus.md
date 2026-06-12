---
title: "Transparant menus"
date: 2008-12-17
forum: General Help
---

### Post by Falc7 on 2008-12-17
I was reading this thread:
[http://ubuntuforums.org/showthread.php?t=262334](http://ubuntuforums.org/showthread.php?t=262334)


And apparently this worked for some people:
Go To
System>Preferences>Advanced Desktop Settings>General>Opacity Settings
add an entry as "dropdownmenu"
Don't use the quotes.
set to around 290
Done!


But i don't seem to have 'opacity settings' in general options

---

### Post by eternalnewbee on 2008-12-17
You are probably using intrepid.
Go to: System > Preferences > CompizConfig Settings Manager, and take it from there.

---

### Post by Falc7 on 2008-12-17
There does seem to be an opacity option there, but i added 'dropdownmenu' and set it to 80, but it isen't transapant

---

### Post by rfurman24 on 2008-12-19
I set mine in compiz config settings manager. In opacity settings add

type=DropDownMenu and a value for the opacity.

---

### Post by eternalnewbee on 2008-12-19
> **Falc7 said:**
> There does seem to be an opacity option there, but i added 'dropdownmenu' and set it to 80, but it isen't transapant
Press **ALT-F2**, and enter ```
compiz --replace

```
Hope that solves it.

---

### Post by escorpiao on 2008-12-19
System > Preferences > CompizConfig Settings Manager > Opacity, Brightness and Saturation, 

Opacity

Window Specific Settings

Windows              |Window Values
type=DropDownMenu    |95

Also, make sure you checkmark Enable Opacity, Brightness and Saturation.  It didnt work for me the first time because I forgot to enable it. lol. Its not enabled by default. :-)

---

### Post by Falc7 on 2008-12-27
haha, yes i forgot to enable it. Thanks

---

### Post by steveneddy on 2008-12-27
Can we mark this as solved please?

---

### Post by pirattrev on 2008-12-28
w00t, I love a good [solved]

---

