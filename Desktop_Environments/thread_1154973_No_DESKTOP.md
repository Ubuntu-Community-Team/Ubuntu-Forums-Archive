---
title: "No DESKTOP"
date: 2009-05-10
forum: Desktop Environments
---

### Post by ceylonerana on 2009-05-10
Hi all. I'm using Kubuntu 8.10. I used it without any desktop effects because I did not install graphic card drivers. My graphic card is Nvidia Gforce MX4000 64MB. Today I enabled desktop effects and after that the whole monitor displays only ash color window :confused:. The curser  displays clearly and that is the only visible object. I want to disable the Desktop effects. Can it do using terminal??? 
I need ur help urgently guys.:)
Thanks.

---

### Post by pro003 on 2009-05-10
you can boot to **Recovery mode** then drop to **root shell** and remove compiz i.e visual effects.

```
# apt-get remove compiz
```

then try to login.

---

### Post by RedSingularity on 2009-05-10
If you cant get in the graphical login type "startx" in terminal.

---

### Post by ceylonerana on 2009-05-10
Thanks both of you. I'll try ur methods and will tell the results. Cheers for ur help.:)

---

