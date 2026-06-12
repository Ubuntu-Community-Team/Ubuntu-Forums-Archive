---
title: "vmware without sound"
date: 2006-09-02
forum: Desktop Environments
---

### Post by hraposo on 2006-09-02
I installed the VMware-workstation-5.5.2-2, but I have no sound. The definitions of sound is /dev/dsp, but I install windows98 in vmware and I still without sound. Why?

---

### Post by kaffelars on 2006-09-02
Is another application using the soundcard?

If I have Rhythmbox or any other application with sound running and start up a virtual machine, I don't get sound there, so that may be it :)

---

### Post by stani on 2006-09-02
Close the other applications one by one and find out which one is blocking it. I experienced that Firefox (or one of its extensions) often blocks my sound card.

Stani

---

### Post by hraposo on 2006-09-02
The's no application blocks the sound card... I think the problem is the definition /dev/dsp...is this the correct device for sound?

---

### Post by cfa on 2006-09-02
maybe this link can help you :

[http://news.u32.net/articles/tag/vmware]("http://news.u32.net/articles/tag/vmware")

---

