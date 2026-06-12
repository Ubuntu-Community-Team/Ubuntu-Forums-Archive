---
title: "Missing encrypt / decrypt context menu items"
date: 2024-10-30
forum: Desktop Environments
---

### Post by noutram on 2024-10-30
In the past, I've seen an option whereby you right-click a file in Nautilus, and there was a context menu option to "encrypt" (using GPG).

In Ubuntu 24.04, this no longer appears (at least, on my machine). Maybe it was a Gnome extension?

Thanks in advance.

---

### Post by deadflowr on 2024-10-30
It was part of a package called seahorse-nautilus which has been removed from 24.04 noble:
[https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/2059269](https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/2059269)

I don't know what alternatives there are outside of the command line to do what it did.

---

### Post by noutram on 2024-10-30
Hi

Thanks for the clarification. Shame this was not resolved for 24.04. For now I've added a couple bash scripts in ~/.local/share/nautilus/scripts/GPG
It is limited to encrypting for myself, but I can live with it.

In case anyone else wants to do the same, here they are:

[B]

Encrypt.sh[/B]
[FONT=Courier New]
#!/bin/bash

# Gnome script to encrypt all selected files

for file in "$@"
do 
    gpg -e -r "me@myemail.org" "$file"
done
[/FONT]


[B]Decrypt.sh
[/B][FONT=Courier New]
#!/bin/bash

for file in "$@"
do 
    gpg "$file"
done
[/FONT]

---

