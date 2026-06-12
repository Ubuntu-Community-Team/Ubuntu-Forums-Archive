---
title: "Hosts: what should it look like?"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-21
"sdfsdf127.0.0.1 localhost"  is what it is now.

"127.0.0.1 localhost.localdomain localhost myusername" is what someone in another thread looked like.

I can't change the file right now as I can't edit the damn thing to add the much needed username, but I have another thread about that. Should I have the localhost.localdomain part instead of sdfsdf when I edit it? Should I simply add the username? Thanks!

---

### Post by Xian on 2005-05-21
Open that file with write priviledges to edit:
```
sudo gedit /etc/hosts
```
Then do as suggested and place this at the top of the file:

127.0.0.1  localhost.localdomain  localhost  <your_machine_name>

This is mine (I juse use linux as my machine name):
127.0.0.1  localhost.localdomain  localhost  linux

---

### Post by Curlydave on 2005-05-21
How would I go about opening it with write privledges? Why are they blocked by default anyhow?

Typing that in the console gives me an empty text editor window and the following message:

sudo: unable to lookup amd64 via gethostbyname()

(gedit:8059): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

** (gedit:8059): CRITICAL **: gedit_cmd_edit_undo: assertion `active_view' failed

---

### Post by Curlydave on 2005-05-21
Nvm: The nice folks on IRC fixed this for me! The issue is that gedit was indeed being messed up by the error I needed to fix with it. VI worked though, and now the hosts file is fixed and gedit works as well.

---

