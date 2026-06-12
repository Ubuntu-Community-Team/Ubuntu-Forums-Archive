---
title: "Totem messed up after update"
date: 2006-04-18
forum: Desktop Environments
---

### Post by linuxNewb on 2006-04-18
Totem has worked fine since Warty. I updated totem via synaptic a few days ago -- the update that removes xine. Since then all videos and even audio runs very slow, and choppy for a few seconds before getting so slow/choppy that it essentially hangs. I have watched video and listened to mp3s with Breezy for months with no problems. Does anyone know what might be causing this, and/or how to fix it? Thanks in advance. Note: my comps specs are below in my signature.

---

### Post by ronmarley1 on 2006-04-18
Dump gstreamer and go back to xine.

---

### Post by Qrk on 2006-04-18
You probably just need to reinstall *totem-xine* though I am perplexed at why the update would want to removel it. 

```
sudo apt-get remove totem-gstreamer
sudo apt-get install totem-xine
```

---

### Post by Efrain Valles on 2006-04-18
Install Totem-xine

or go automatix...

---

