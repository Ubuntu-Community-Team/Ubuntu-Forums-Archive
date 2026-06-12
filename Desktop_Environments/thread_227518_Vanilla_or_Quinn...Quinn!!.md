---
title: "Vanilla or Quinn?...Quinn!!"
date: 2006-08-01
forum: Desktop Environments
---

### Post by tpnerdcore on 2006-08-01
hello all. I have a quick question. Is it possible to switch from Compiz-Vanilla to Compiz-Quinn? I have compiz vanilla installed using a guide that i cannot find anymore. So if its not possible to install quinn over vanilla, then how can i undo and start over with the GDM defaults so i can try another guide?

thanks for reading and thanks for your help

-anthony

---

### Post by reacocard on 2006-08-01
if you're using the compiz repos, its dang easy to install over. just search synaptic for compiz and install quinn's packages.

---

### Post by jstueve on 2006-08-01
installing quinn from quinn's repository will remove vanilla... 

and...

installing vanilla from quinn's repository will remove quinn...

makes sure you install compiz and compiz-gnome (or compiz and cgwd if you want to have customized themeing)

---

### Post by tpnerdcore on 2006-08-02
thanks all, ill try to install from quinns repos. Ill keep you updated. Thanks for the help.

-anthony

---

### Post by tpnerdcore on 2006-08-02
can someone please point me to the repos needed. I thought i found the right repos but all i see in synaptic are updated Compiz-vanilla packages. thanks

-anthony

---

### Post by tpnerdcore on 2006-08-02
haha spoke to soon, i got quinn installed and gcompize themer up and going. I have to do "cgwd --replace" at startup to start it up though, and i get "cannot open pixmap" error. Any ideas on that. Thanks

-anthony

---

### Post by mcduck on 2006-08-02
> **tpnerdcore said:**
> haha spoke to soon, i got quinn installed and gcompize themer up and going. I have to do "cgwd --replace" at startup to start it up though, and i get "cannot open pixmap" error. Any ideas on that. Thanks

-anthony
I don't know about the pixmap error, seems to be quite common one so you could check from the compiz forums.

For the cgwd thing, edit the script you use to start compiz and replace every 'gnome-window-decorator' with 'cgwd' and you don't need to start it yourself any more :)

---

### Post by tpnerdcore on 2006-08-02
thanks that works!! thanks so much!!

-anthony

---

