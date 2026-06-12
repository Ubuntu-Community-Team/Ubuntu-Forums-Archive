---
title: "apt-get/synaptic, blocking certain packages?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by kirky3000 on 2005-08-09
Hi There

I have installed a .deb package that wasn't in the ubuntu repositories. It had one dependency problem, I can't solve the dependency issue but my new program works anyway.

But apt-get/synaptic are reporting it as broken, everytime I do an upgrade or install a new program. Is there a way I can make apt-get/synaptic just ignore this one broken package and stop trying to fix it?

Cheers

---

### Post by az on 2005-08-09
sudo apt-get -f install

---

### Post by kirky3000 on 2005-08-09
that will just remove the broken package. I want the broken package installed but for apt-get to just ignore it  i.e. stop telling me its broken

Cheers

---

