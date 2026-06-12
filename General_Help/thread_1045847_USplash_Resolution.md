---
title: "USplash Resolution"
date: 2009-01-20
forum: General Help
---

### Post by DOSIX on 2009-01-20
My usplash resolution too high. the letters come out humongous and it warps to the other side of the screen. i know what the problem is, i just forgot the location of the file that contains the usplash resolution. can someone please give me the path?

---

### Post by dcstar on 2009-01-20
> **DOSIX said:**
> My usplash resolution too high. the letters come out humongous and it warps to the other side of the screen. i know what the problem is, i just forgot the location of the file that contains the usplash resolution. can someone please give me the path?

/etc/usplash.conf, and do this after any change:

```
sudo update-initramfs -k all -u
```

---

### Post by DOSIX on 2009-01-24
thank you

---

### Post by TrenTech on 2009-02-03
I changed my usplash today and noticed that the they come out smaller than my screen. aparently it's always been like this I just couldn't tell because of the black ubuntu usplash. the usplash.conf is set to 1920x1200 which is correct to my screen size, so why don't they stretch to my screen size???? really would like to fix this.

---

### Post by TrenTech on 2009-02-03
nevermind. I set the res to 1024x786 and it fixed the problem. sweet!

---

### Post by dcstar on 2009-02-03
> **TrenTech said:**
> I changed my usplash today and noticed that the they come out smaller than my screen. aparently it's always been like this I just couldn't tell because of the black ubuntu usplash. the usplash.conf is set to 1920x1200 which is correct to my screen size, so why don't they stretch to my screen size???? really would like to fix this.

There are only a very limited number of resolutions that usplash supports.

---

