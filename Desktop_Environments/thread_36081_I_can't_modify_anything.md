---
title: "I can't modify anything"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-21
I'm trying to modify my hosts file because I keep getting errors about doing anything because of an error, which I've researched, where the installer didn't add my user name to the hosts file. I want to add it at the end of the line, but I can't as it's read only, and I apparently don't own it so I can't change the permissions.  :? 

What's up? How can I modify the file?

---

### Post by f.prisson on 2005-05-21
This file can only be edited by root. Open it with```
sudo gedit /etc/hosts
```

---

### Post by Curlydave on 2005-05-21
That does the same thing as opening it through "Computer"; it still won't edit.

edit: even more puzzling: I just did it again and this time it opened a blank text eitor adn gave me this error:



sudo: unable to lookup amd64 via gethostbyname()

(gedit:8059): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

** (gedit:8059): CRITICAL **: gedit_cmd_edit_undo: assertion `active_view' failed



the first error is what I"m trying to fix; is this causing the other problems?

---

### Post by mherring on 2005-05-22
first, open a terminal and type "su" to become root.  In /etc, type ls -l for a long listing.  First change owner and group as required, and then change the permissions.

If this is all greek, try "man chown", and "man chmod"

In the terminal, type "more <filename>" just to be sure that you can read the file

If you have not yet activated the root account:

sudo passwd root

enter YOUR password at the prompt, then a NEW password for the root account.


BTW, I do not like the way Ubuntu sets up the initial user with some powers and then disables root.

---

