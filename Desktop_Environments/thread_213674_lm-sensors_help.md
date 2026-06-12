---
title: "lm-sensors help"
date: 2006-07-11
forum: Desktop Environments
---

### Post by nami on 2006-07-11
Hi

I have been trying to get lm-sensors / gdesklets to work on my system but am having no luck.  I can get gdesklets to work but any gdesklets which use onboard sensors don't work.

I have the following board: [http://www.dabs.com/ProductView.aspx?Quicklinx=3M75](http://www.dabs.com/ProductView.aspx?Quicklinx=3M75)

Does anyone know if lm-sensors will work with my board?

Thanks

nami

---

### Post by angkor on 2006-07-11
Have you tried running:

```
sudo sensors-detect
```

---

### Post by pointym5 on 2006-07-11
I'm having the problem that "sensors-detect" fails with "No i2c device files found".

---

### Post by angkor on 2006-07-12
> **pointym5 said:**
> I'm having the problem that "sensors-detect" fails with "No i2c device files found".

Read [this howto]("http://ubuntuforums.org/showthread.php?t=2780") to fix that error. You need to run the mkdev.sh script.

---

