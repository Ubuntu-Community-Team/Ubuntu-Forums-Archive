---
title: "I cannot create new folder inside /opt directory"
date: 2010-06-16
forum: Desktop Environments
---

### Post by subakaran on 2010-06-16
Hi ,all
am new in ubuntu.
I have Administrator rights. 
I want to create new folder into /opt directory.
So i clicked(Right click). but new folder menu has disabled. I cannot create new folder.

Then Alternatively I used terminal. then I type mkdir /opt/lampp/htdocs/dummy
now folder name has created. but I cannot paste anything into my dummy folder.
So I checked permission which has you are not owner.

Please advice to me.
How to create new folder & copy contents to new folder.
please.
Thanks.

---

### Post by oldos2er on 2010-06-16
Either use "sudo" in the terminal, e.g. ```
sudo mkdir /opt/foo
``` or run ```
gksu nautilus
``` to open Nautilus with admin privileges.

---

