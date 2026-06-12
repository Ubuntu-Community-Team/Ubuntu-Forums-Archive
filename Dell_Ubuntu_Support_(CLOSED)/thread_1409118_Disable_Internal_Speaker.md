---
title: "Disable Internal Speaker"
date: 2010-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mosquetero on 2010-02-17
Hi everyone!

Everytime I type in my console and I use the tab to write faster, there is an annoying BEEP! coming out from my computer. This prevents me from using my laptop in public places since I have no idea of how to disable it. Can you help me please?? I am not really sure if I msut solve it using the BIOS but anyway I post it here.

I have a Dell D620 laptop.

Thanks in advance!

---

### Post by mosquetero on 2010-02-17
I found a solution!!

```
sudo modprobe -r pcspkr 
```

---

### Post by gvoima on 2010-02-17
You could also disable the terminal bell for the terminal you're using.

---

### Post by mikewhatever on 2010-02-17
> **mosquetero said:**
> I found a solution!!

```
sudo modprobe -r pcspkr 
```

You can add the module to /etc/modprobe.d/blacklist.conf to prevent it from loading.

---

