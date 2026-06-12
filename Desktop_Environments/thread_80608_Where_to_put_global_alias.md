---
title: "Where to put global alias?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by RoyCowboy on 2005-10-22
I want Firefox to run gnome-btdownload with certain parameters. Is it possible to create an alias for the command in some file? I've tried ~/.bashrc and /etc/bash.bashrc but I guess that they are only for shell logins..
Can anyone help me out?

---

### Post by Goofy_2 on 2005-10-23
Try e.g. this.

Put at the end of /etc/bash.bashrc  a line like:

       alias monkey=' "echo "a BIG one" '

Restart your PC with or without X and enter the command:

       monkey

:cool:

---

### Post by RoyCowboy on 2005-10-23
As I wrote in my first post I have tried /etc/bash.bashrc but the alias will only work in terminal. If I tell Firefox to use your monkey-alias it will do nothing because it's only available from a terminal..

---

