---
title: "Copy &quot;command&quot; for keyboard shortcut?"
date: 2010-07-20
forum: Desktop Environments
---

### Post by wahr on 2010-07-20
Hi, this question is simple, but I've done some google-fu and wiki hopping and haven't found much on it.

I use a variety of text editors and web browsers with SSH often, and I want to bind my text copy/paste to windows+c/windows+v combos at the global level for better workflow (ctrl c has it's obvious problems in this scenario).

I went to create a custom keyboard shortcut (which will hopefully override individual apps as well), and it asks for the command. anyone know this one?

---

### Post by Richard Creek on 2010-10-24
Hi wahr, i've been looking everywhere for this too.

I found the command to make it work using xbindkeys and xbindkeys-config

This will send the command to copy (ctrl+c)
xvkbd -xsendevent -text "\[Control]\c"

This will send the command to paste (ctrl+v)
xvkbd -xsendevent -text "\[Control]\v"

This will send the command to cut (ctrl+x)
xvkbd -xsendevent -text "\[Control]\x"

For anyone struggling to get their logitech G11 custom keys working this seems a good solution.  The g15macro was working for me until lucid, and then it wouldn't save keys between reboots.

---

