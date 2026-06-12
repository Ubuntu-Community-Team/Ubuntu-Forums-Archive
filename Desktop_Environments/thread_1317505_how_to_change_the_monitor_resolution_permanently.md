---
title: "how to change the monitor resolution permanently?"
date: 2009-11-06
forum: Desktop Environments
---

### Post by nusry on 2009-11-06
Hi guys..... am very new to ubuntu OS..

So am encountering some problems which may seem simple to u.. any way just help me out to work out with ubuntu..

The problem is : my monitor resolution setting was 1280 * 1024 it's not suites to my monitor.. so I've changed it to 1024 * 768 it works.. but evry time I restart the machine I have to change the settings coz it automatically changes to default resolution (1280 * 1024) so how can I solve this problem (how to make 1024 * 768 as the permanent resolution)??

---

### Post by wojox on 2009-11-06
What graphics card you using or how are you setting this up?

---

### Post by nusry on 2009-11-06
my graphic card is nVidia 7200GS..
I have installed vga drivers....

am doing this by going to Nvidia X server Settings (System >> Administration >> Nvidia X server Settings)

---

### Post by wojox on 2009-11-06
Open a terminal:

```
gksudo nvidia-settings
```

You need to be root to make it stick.

---

### Post by nusry on 2009-11-06
tnx bro.. it worked....

---

### Post by wojox on 2009-11-06
Cool

---

