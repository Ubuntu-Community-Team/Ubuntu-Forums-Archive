---
title: "made 192 desktops... crap..."
date: 2009-01-23
forum: General Help
---

### Post by Bandanna on 2009-01-23
Ummm, We'll you see... I was in compiz and I was actually going to bring my horizontal desktop number from 6 to 4 but I accidently clicked the right side of the vertical desktop slide, thus changing the amount of verticle rows to 32.
I wasn't paying attention and the changes took place within the second after I clicked the slider...

Needless to say My ubuntu account is locked up. My comp just cant handle 192 desktops, ya' know.:-|

Is there a way to access compiz through a terminal in the recovery boot and set the settings to default under my account???

-ubuntu 8.10-

---

### Post by sandyd on 2009-01-23
please be carefull.....

```

gconftool-2 –recursive-unset /apps/compiz

```

this should fix it. (and i hope you have gnome installed somewhere on your comp)

---

### Post by cariboo on 2009-01-23
You could probably delete ~/.compiz in your home directory and get back to your normal desktop, By doing this all your compiz settings will be gone.

Jim

---

### Post by Bandanna on 2009-01-23
actually,
gconftool-2 -recursive-unset /apps/compiz 
code would not work said that -recursive-usnet was unrecognized command

I googled after I saw you're posts one more time and Just ended up using
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

