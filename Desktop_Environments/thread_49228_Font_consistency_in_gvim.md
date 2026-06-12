---
title: "Font consistency in gvim"
date: 2005-07-15
forum: Desktop Environments
---

### Post by rosslaird on 2005-07-15
I use kde, gnome and xfce (depending on my mood). And I use gvim as my editor. When I use gvim in gnome, the correct font is used (Bitstream Vera Sans Mono 12). Gvim seems to pay attention to the settings in gnome-font-properties. But when I run gvim in kde or xfce, it defaults to a smaller, 11 point version of the font. In KDE, when I run gnome-font-properties and then run gvim, it corrects to the proper font. (I have tried Kvim and it also uses the 11 point version, and I have found it impossible to change this without the application freaking out by endlessly resizing the window.)

What I want is for the gvim font to be consistent, by default, no matter which environment I'm using. I have tried various ways of specifying the font in my .vimrc file, as indicated on the vim mailing lists, but none of those methods has worked at all. It seems like the application looks for and uses the font settings in gnome but not in KDE (when I change the font in the KDE control panel it does not affect gvim or kvim).

I do have gtk2-engines-gtk-qt installed. It seems to have no effect on gvim.

Any suggestions?

Ross

---

### Post by f20cap1 on 2005-07-15
Try setting the font in your .gvimrc

Something like this:
```
set gfn=Bitstream\ Vera\ Sans\ Mono\ 12
```

---

### Post by rosslaird on 2005-07-15
I did not have a .gvimrc (just .vimrc), so I created one in my home directory, added the line, and ---
it worked!

Gosh, why was it so hard to do that? I have browsed and searched the vim pages for hours trying to get this to work, and not once did I see a reference to a .gvimrc file.

Thanks for the help.

Ross

---

