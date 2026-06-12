---
title: "Need to open a a terminal by right clicking... how do I do this?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by cobbweb on 2006-09-20
Hey, 
 
 I know there is a plugin or a program that does this, but I would like to be able to right click in the directory that im in and open a terminal in that directory. Also, I once had it set up where I could right click on a tar'ed file and it would "Extract Here" the file for. How do I get my desktop set up like that? 
 
 Thanks, 
 
 Cobbweb

---

### Post by AZzKikR on 2006-09-20
Hint: take a look at the directory in your home folder:

~/.gnome2/nautilus-scripts/

Every executable script you put in there is accessible with the right click menu!

---

### Post by neymac on 2006-09-20
Open synaptic and search: nautilus-open-terminal
Install it.

---

### Post by Omnios on 2006-09-20
Hi hi just whiped this one out from memory.

 Script text. 

```

#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

```

 Right click scripts are stored in. /home/tom/.gnome2/nautilus-scripts.
Create a empty document and enter the above text and sava as say terminal. ALso you have to ser permitions to executable.

---

### Post by cobbweb on 2006-09-20
So if I wanted to be able to open the Ubuntu System Panel by just right clicking I can just make a scrip that opens the system panel and put it into that file? Will this work for right clicking on the Desktop too? 

Cobbweb

---

### Post by neymac on 2006-09-20
With the package "nautilus-open-terminal" installed, the right-click gives option to "open terminal" or "Extract here" at Desktop or at any folder opened with Nautilus.

See [http://packages.ubuntulinux.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=nautilus-open-terminal](http://packages.ubuntulinux.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=nautilus-open-terminal)

---

### Post by kpkeerthi on 2006-09-20
Useful tip. Thank you guys.

---

