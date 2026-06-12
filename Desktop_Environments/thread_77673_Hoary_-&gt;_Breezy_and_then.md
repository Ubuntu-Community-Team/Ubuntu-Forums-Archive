---
title: "Hoary -&gt; Breezy and then??"
date: 2005-10-17
forum: Desktop Environments
---

### Post by lawi on 2005-10-17
Hi all,
I did a dist-upgrade from Hoary to Breezy and after fixing some xorg stuff everything is up and running :D 

So to my question: Is there a way to remove/check old stuff from hoary or is everything taken care of during upgrade??

BR,.
lawi

---

### Post by Leif on 2005-10-17
there is deborphan that will tell you which packages are not being used by anything else :

sudo apt-get install deborphan
sudo deborphan

I wouldn't trust this 100% though, so be careful what you delete.

---

