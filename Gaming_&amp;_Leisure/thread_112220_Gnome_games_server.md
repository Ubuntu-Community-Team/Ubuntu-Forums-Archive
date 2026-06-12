---
title: "Gnome games server"
date: 2006-01-03
forum: Gaming &amp; Leisure
---

### Post by samuelgs on 2006-01-03
Hi,
I've just been experimenting with some of the games in Ubuntu 5.10 as I am impressed enough with Ubuntu to make it the primary OS instead of winXP on my home network. There is a problem I have encountered though, Iagno (Application-->Games-->Iagno) has the option for a network game, but the dialog box requests a Gnome games server. I've been searching through Synaptic, Ubuntu support and even the Gnome website and can't find any reference to the Gnome Games Server. What I would like to know is where I can find it so that I can install it.

[IMG]http://samuelgordonstewart.com/wp-content/non-wp-files/IagnoNewNetworkGame.png[/IMG]

I'm sorry if this has been discussed before, but I couldn't find anything about it.

Thanks,
Samuel

---

### Post by fatsheldon on 2006-11-11
not sure if this thread is still active... but I had the same question.

The answer: run this:  game-server.py


It runs a little daemon and I was able to connect to it from the local machine and another on the network and destroy my 5-year old at network nibbles.  w00t!

fatsheldon

---

### Post by samuelgs on 2006-11-11
Thank you very much fatsheldon. I'll admit that I had forgotten all about this thread, so the reply notification in my email was a very pleasant surprise.

Thanks again fatsheldon

---

### Post by WaddleDee on 2008-01-24
Where do I find game-server.py? I googled it, and I get 2 results. This and another site.

Please help! (Srry for bumping)

---

### Post by picpak on 2008-08-16
Old thread, I know, but you need to install ggzd:

```
sudo apt-get install ggzd
```

---

