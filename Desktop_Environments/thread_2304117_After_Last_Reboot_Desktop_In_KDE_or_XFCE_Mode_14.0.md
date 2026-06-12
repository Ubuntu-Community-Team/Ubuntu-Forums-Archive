---
title: "After Last Reboot Desktop In KDE or XFCE Mode 14.04.3"
date: 2015-11-24
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-11-24
Hello,

After the last reboot my system switched to a completely different look, with a different windowing scheme and font. It looks like KDE or XFCE. How do I get back?

Thanks, Hannibal

---

### Post by Frogs Hair on 2015-11-25
Do you have multiple desktop environments installed ?

---

### Post by coljohnhannibalsmith on 2015-11-26
> **Frogs Hair said:**
> Do you have multiple desktop environments installed ?

No; but I have k3b installed, because it is the least buggy burner I've been able to find.

I've had this problem in the past with other distros; and the problem seems to have been one of bit-rot. So, I tried rebooting twice; and when that didn't help, I did an update and rebooted again. The windowing environment returned to normal; but I'd like to know what caused it and how to prevent it from happening again.

---

### Post by Frogs Hair on 2015-11-26
My guess is that the application brings a large number of KDE dependencies with and other than reseting compiz or rebooting there might not be much you can do.

---

### Post by coljohnhannibalsmith on 2015-11-26
> **Frogs Hair said:**
> My guess is that the application brings a large number of KDE dependencies with and other than reseting compiz or rebooting there might not be much you can do.

How do I reset Compiz?

Thanks, Hannibal

---

### Post by Frogs Hair on 2015-11-26
```
sudo apt-get install dconf-editor  
``````
 dconf reset -f /org/compiz/
```

---

### Post by coljohnhannibalsmith on 2015-11-26
> **Frogs Hair said:**
> ```
sudo apt-get install dconf-editor  
``````
 dconf reset -f /org/compiz/
```

Danke

Oh, and I think I'll make a button for this! It should really have one.

---

