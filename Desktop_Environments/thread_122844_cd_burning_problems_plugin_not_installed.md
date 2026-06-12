---
title: "cd burning problems plugin not installed"
date: 2006-01-28
forum: Desktop Environments
---

### Post by kasemodz on 2006-01-28
alright i want to burn an audio cd. So first when i popped the blank cd i selected that option. It opened serpentine, then i tried adding the mp3 files and it said this fil is not supported. So then i installed gnomebaker and tried burning an audio cd and it said the plugin to handle audio/mpeg is not installed. What am I missing here?

---

### Post by kingsidy on 2006-01-28
install lame: sudo apt-get install lame
gstreamer0.8 lame search for this in synaptic
gstreamer0.8 plugins look for this in synaptic as well
better yet used automatic and install audio codecs

---

### Post by cogumbreiro on 2006-04-02
Actually, you need to install gstreamer0.8-mad

---

### Post by ronmarley1 on 2006-04-02
Additionally, I use K3b to burn/copy CDs.  It also requires the cdrdao package.  Both are available in the repos.  I like K3b a lot more than gnomebaker.

---

### Post by merlyn on 2006-04-04
[quote=cogumbreiro]Actually, you need to install gstreamer0.8-mad[/quote]

Cool, just the answer that I was looking for.

Works a treat by the way.

Thanks mate.

---

