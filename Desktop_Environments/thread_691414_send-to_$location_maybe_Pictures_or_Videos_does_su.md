---
title: "send-to $location /maybe Pictures or Videos? does such a thing exist?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by puccaso on 2008-02-08
so i am looking for a way to 
create a right-click option in nautilus that will allow me to select, right click - send too - then have pre set locations.. pictures, videos, etcetc
does such a thing exist?

can anyone else...?

---

### Post by tcommbee on 2008-02-08
why not use the "places" sidebar for that (isn't drag'n'drop a nice thing to have :) )? alternatively you could write some nautilus-actions, but i think they can't be grouped in a subfolder in the context menu.

---

### Post by puccaso on 2008-02-08
yep
the 2nd part of ur comment explained my issue

being able to right click onto a file and say send to>(somewhere) is much easier - especially from the desktop and if ur using spacial mode and not browse (which slows things down iv noticed)


nautilus-actions 

there must be an easier way

---

### Post by tcommbee on 2008-02-08
This might be useful: [http://library.gnome.org/users/user-guide/latest/gosnautilus-444.html.en](http://library.gnome.org/users/user-guide/latest/gosnautilus-444.html.en)

a script might then look like:
#!/bin/bash
foreach filename in "${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS}" do
{
    mv "$filename" ~/Music
} done

i haven't done much shell-scripting yet, so this could be syntactically completely wrong. anyway, the advantage is, that all those scripts are in a common "scripts"-submenu in the context menu

---

