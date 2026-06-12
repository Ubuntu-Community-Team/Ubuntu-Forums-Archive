---
title: "Ubuntu11.10 Gnome 3 Shell Restarts on Activity Search"
date: 2012-02-18
forum: Desktop Environments
---

### Post by GeraldNunn on 2012-02-18
There was a gnome update not too long ago and ever since then I've been experiencing an annoying issue where the Gnome 3 shell will restart when searching for applications that start with the letter 'r' like Remmina. Normally if you press the Alt-F2 and type in 'r' and enter the shell restarts and that's fine, but now when you hit the windows key if the first letter I type when searching for an application is 'r' the gnome shell restarts instead of showing apps that start with 'r', it's very annoying.

Is this a bug and is there some setting I can change to disable this behavior?

---

### Post by karsta62 on 2012-02-21
I can verify this behaviour (Mint 12 though). Immediately when pressing the first letter to search it restarts gnome shell. Fedora 15 does it as well. Not sure about Fedora 16.

---

### Post by Frogs Hair on 2012-02-21
Search the forum because you are not alone . I don't know if this has been resolved for other users or not .

---

### Post by karsta62 on 2012-02-21
Found a workaround from a spanish page ([http://www.taringa.net/posts/linux/14061303/Gnome-Shell-creashea-cuando-buscas---Nvidia.html](http://www.taringa.net/posts/linux/14061303/Gnome-Shell-creashea-cuando-buscas---Nvidia.html)).

In short:

(Run manually first to see it works and then) put this in startup programs:
echo ""> ~/.local/share/recently-used.xbel

Just a workaround though, but works for me.

---

