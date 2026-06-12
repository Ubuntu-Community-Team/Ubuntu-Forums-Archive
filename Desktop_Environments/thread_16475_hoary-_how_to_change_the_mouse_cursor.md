---
title: "hoary- how to change the mouse cursor?"
date: 2005-02-21
forum: Desktop Environments
---

### Post by T31 on 2005-02-21
someone knows how to change the hoary mouse cursor,for the warty one?

this one is quite ugly and i loved the former one

thx

---

### Post by kassetra on 2005-02-21
[QUOTE=T31]someone knows how to change the hoary mouse cursor,for the warty one?

this one is quite ugly and i loved the former one

thx[/QUOTE]

Yep.  Unzip [this file]("http://www.linuxpeach.com/ubuntu/cursors.zip") & drop the directory into the /usr/share/icons/THEME_currently_using/
:)

(if you hate the new ones, then overwrite the cursors directory)

---

### Post by Solon on 2005-02-21
In addition to the post above, you should download gcursor from the repositories, once installed, you can change your cursors to you heart content, and also go to [www.gnome-look.org](www.gnome-look.org) and find any cursor you want for X11. I personally like Ptux's cursors, even has one set for Ubuntu itself. BTW: Gcursor, after installation, should be under Preferences, and be called "Cursor Selection".

---

### Post by KLineD on 2005-02-21
Also if you have a Warty CD, you can add that CD to the apt repositories (you can do it in synaptic) and then search for gtk2-engines-industrial. Select the package and then go to the Package menu and select Force version. Choose the warty one and there you go.

Be aware that if you upgrade the system that package will get upgraded also and thus you loose the cursors again. To solve it, just lock the package once installed. To lock it in synaptic use the Package menu also.

---

### Post by graigsmith on 2005-02-27
those old cursors were so pretty. i dont like the new ones,  theres also a missing theme :(  it had rounded edges, anyone know what that was called?

---

### Post by t.rei on 2005-02-27
Industrial?

or the ubuntu one "Human"

---

### Post by Simon211065 on 2005-03-05
[QUOTE=kassetra]Yep.  Unzip [this file]("http://www.linuxpeach.com/ubuntu/cursors.zip") & drop the directory into the /usr/share/icons/THEME_currently_using/
:)

(if you hate the new ones, then overwrite the cursors directory)[/QUOTE]
Kassetra,

Could you possibly assist? I have a mouse dilemma but one where the pointer just won't move. I've been to the installation forum and they have suggested to edit the F86Config. This I've tried with HWCursor false and SWCursor true but neither worked. Could you suggest something else?

---

