---
title: "Change button positions"
date: 2012-03-14
forum: Desktop Environments
---

### Post by Ralph L on 2012-03-14
Just installed oneiric and gnome-session-fallback.  Since I use Windows XP about half the time I would like to keep my oneiric user interface similar to XP.  So I would like to change position of the minimize, maximize, close buttons from left to right.  I found a web site ([http://www.matbra.com/en/2011/10/13/mudando-a-posicao-dos-botoes-do-menu-no-ubuntu-11-10/](http://www.matbra.com/en/2011/10/13/mudando-a-posicao-dos-botoes-do-menu-no-ubuntu-11-10/)) that says to change gconf-editor>apps>metacity>general>button_layout.  Tried to do that but gconf-editor said it couldn't be done and that I needed a newer version.

Can anybody help me a newer version, or tell me some other way to change it.

Ralph

---

### Post by Ralph L on 2012-03-14
Just found this on [http://www.matbra.com/en/2011/10/13/mudando-a-posicao-dos-botoes-do-menu-no-ubuntu-11-10/](http://www.matbra.com/en/2011/10/13/mudando-a-posicao-dos-botoes-do-menu-no-ubuntu-11-10/) .

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string
":minimize,maximize,close"
```

It worked.

---

