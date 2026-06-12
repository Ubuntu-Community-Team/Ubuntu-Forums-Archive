---
title: "Cairo-Dock, GPG: no valid openPGP data found."
date: 2010-02-02
forum: Desktop Environments
---

### Post by EizoSiege on 2010-02-02
Hi, I am trying to install Cairo Dock. I am following a tutorial but I have stumbled upon a problem.

I have added this to my sources.list:

"deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock"

I then try to add the signed GPG key with this command: 

"wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -"

But I get this error:
"luke@luke-laptop:~$ wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -
"

Can someone help me with this. I really want the cairo dock.


Any help will be much appreciated.

---

### Post by fabounet on 2010-02-02
not sure but currently the repository is down, so it may be the reason.
to install it, you should use the PPA repository on launchpad.

---

