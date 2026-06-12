---
title: "File manager opening very late &amp; with warning"
date: 2012-10-21
forum: Desktop Environments
---

### Post by linuxyogi on 2012-10-21
When I double click the Home icon or click on the file browser (accessories menu) thunar takes along time open  & it opens with the following warining  :

```
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```Thats the problem.

---

### Post by jerrrys on 2012-10-21
Try opening thunar in terminal; what errors do you get there?

---

### Post by linuxyogi on 2012-10-21
> **jerrrys said:**
> Try opening thunar in terminal; what errors do you get there?

I tried opening thunar in Terminal. It just takes a long time to open. No error message.

---

### Post by jerrrys on 2012-10-21
My best guess (I use nautilus) would be to reinstall (maybe purge) thunar.  If you have  customized it, you could backup .config/Thunar/uca.xml or even the whole  .config/Thunar file.

Perhaps a "X" user will come along with a better idea.  Good luck

---

### Post by mike555 on 2012-10-21
I found a work around by setting AutoMount=false in /usr/share/gvfs/mounts/network.mount

---

### Post by Merrattic on 2012-10-21
As mike555 says see here:

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

---

### Post by linuxyogi on 2012-10-21
> **mike555 said:**
> I found a work around by setting AutoMount=false in /usr/share/gvfs/mounts/network.mount

> **Merrattic said:**
> As mike555 says see here:

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

Thanks. The workaround worked.

---

