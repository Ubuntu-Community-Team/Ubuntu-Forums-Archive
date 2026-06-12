---
title: "beryl crashes ubuntu and xubuntu"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by codemyster on 2007-05-10
I've tried this with both Ubuntu (running Gnome) and Xubuntu (running Xfce)

I have installed Beryl and emerald with these commands:

> 
Sudo apt-get install beryl beryl-manager emerald emerald-themes


and i have installed both Beryl and Emerald. Great.

Now, i tried running Beryl manager by going to apps-->System Tools-->Beryl Manager. It shows the Beryl icon in the top bar, but then in crashes.

So then i thought, Maybe this might work

> 
beryl --replace


It doesn't crash but my entire screen is covered in white. When i move the mouse to the center of the screen, i get the little "I" cursor as if there was a text box. 

Does anyone know why Beryl is being a #-o #-o :icon_frown: :x :redface: ?

---

### Post by ra3don on 2007-05-16
same problem! it sucks

---

### Post by Legionzero on 2007-06-06
Yep.  I'm having the same problem. :(

---

### Post by Pekay on 2007-06-06
I'm only getting it for Xubuntu :/.

EDIT: thanks to another thread, a post by psyke83 has this that works for me:

> Add to 'Section "Device"' of xorg.conf:

```


Option "XaaNoOffscreenPixmaps" "true"

```


---

