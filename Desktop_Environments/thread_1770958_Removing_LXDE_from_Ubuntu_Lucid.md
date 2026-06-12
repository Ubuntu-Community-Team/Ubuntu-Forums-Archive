---
title: "Removing LXDE from Ubuntu Lucid"
date: 2011-05-29
forum: Desktop Environments
---

### Post by blauendonau on 2011-05-29
Hi, it's me again! :p I can't resist experimenting with my Linux system, recently I installed the LXDE desktop environment for fun after hearing some good things about it, using:

```
sudo apt-get install lxde
```Now I'd like to remove it. (I have Ubuntu 10.04.) LXDE isn't my cup of tea, plus my application/system menus became more cluttered in GNOME. I know that "apt-get remove lxde" won't work since that package simply "points" to other packages. Will using autoremove do the trick? Installing LXDE took up about 50 MB but I'm told autoremoving will free 70 MB, so I'm concerned it'll be removing other stuff than what I installed. So what is the correct way to remove LXDE without touching anything else? Thanks!

---

### Post by blauendonau on 2011-05-30
Thread bump. Anyone? :)

---

### Post by flick on 2011-05-30
sudo apt-get remove lxde 

sudo apt-get autoremove

Should do the trick. Because :

autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed.

---

### Post by snowpine on 2011-05-30
Follow these instructions to remove LXDE (Lubuntu) and revert to a "pure" Gnome:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by blauendonau on 2011-05-30
> **snowpine said:**
> Follow these instructions to remove LXDE (Lubuntu) and revert to a "pure" Gnome:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Thanks for the link! I've actually looked at that page, but it says the instructions are only applicable for Natty Narwhal so I was a little afraid to try it. But "apt-get autoremove lxde" is safe too, no? Just want to make sure.

---

### Post by snowpine on 2011-05-30
> **blauendonau said:**
> Thanks for the link! I've actually looked at that page, but it says the instructions are only applicable for Natty Narwhal so I was a little afraid to try it.

Sorry:
[http://www.psychocats.net/ubuntu/puregnomelucid](http://www.psychocats.net/ubuntu/puregnomelucid)

---

### Post by blauendonau on 2011-05-30
> **snowpine said:**
> Sorry:
[http://www.psychocats.net/ubuntu/puregnomelucid](http://www.psychocats.net/ubuntu/puregnomelucid)

Heh, I saw that page too, actually, but lubuntu isn't listed. :roll:

---

### Post by blauendonau on 2011-05-30
OK, I think I removed completely it via "apt-get autoremove lxde", which is what I should have simply done in the first place. GNOME seems to be intact. Thread marked as RESOLVED, thank you.

---

