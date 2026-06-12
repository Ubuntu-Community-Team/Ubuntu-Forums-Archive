---
title: "I can't make .Xresources work (here with emacs)"
date: 2009-05-22
forum: General Help
---

### Post by loup.vaillant on 2009-05-22
Hello, I've just installed ubuntu 9.04 and the latest emacs (namely, emacs-snapshot) from synaptic. I wanted it to use antialiased fonts.

Now, the problems lies in the default emacs font: HUGE. No problem, I will change this, with, say, [FONT=Courier New]M-x set-default-font[/FONT]… No luck so far. I didn't even found monospace in the autocompletion list (I may have missed it). Then, I tried with .Xresources:

[FONT=Courier New]Emacs.geometry: 20*5
Emacs.FontBackend: xft
Emacs.font: -monospace 5[/FONT]

Of course, I did
[FONT=Courier New]$ xrdb -merge ~/.Xresources
[/FONT] 
No efect whatsoever. I tried invoquing emacs with "emacs" "emacs-snapshot", and "emacs-snapshot-gtk", the huge font is still there, the geometry is still the default 80 collumns. The only thing that worked so far were
[FONT=Courier New]$ emacs-snapshot-gtk -fn "monospace-5"
[/FONT] 
(Also work with "emacs" and "emacs-snapshot".)

I don't want to just set-up an alias, it wouldn't work very well with the Gnome GUI (menus like "open with").

So, how can I make this .Xresources work?
Thanks.

---

### Post by loup.vaillant on 2009-05-22
Sorry for the noise, then.

Out of curiosity, I have another question, though: why everyone reacheble by our favorite search engine uses .Xresources, while for me, only .Xdefaults works? If someone has a pointer to the intricacies of X configuration, that would be cool.

---

### Post by Tilgovi on 2009-09-23
In case anyone else gets confused by this, you just need to merge it into the current resource database:

xrdb -merge ~/.Xresources

Then it should work.

---

