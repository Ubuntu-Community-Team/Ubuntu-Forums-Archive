---
title: "Downloading OpenSesame software onto Chromebook using Ubuntu"
date: 2019-03-04
forum: Education &amp; Science
---

### Post by sergerya on 2019-03-04
I've downloaded the Ubuntu operating system onto my Chromebook and am trying to download the OpenSesame software, but the code from the download website keeps giving me an error. I don't really know how to code and I don't know anything about Ubuntu, but I need this software for my class. The website for the download is [https://osdoc.cogsci.nl/3.2/download/#ubuntu](https://osdoc.cogsci.nl/3.2/download/#ubuntu) and I believe I have Xenial.

---

### Post by DuckHook on 2019-03-04
Welcome to the forums, sergerya.

Please clarify the following:> **sergerya said:**
> I've downloaded the Ubuntu operating system onto my Chromebook
Do you mean that you have *installed* Ubuntu onto your chromebook? It is not enough to just download it.
> …trying to download the OpenSesame software, but the code from the download website keeps giving me an error.
[LIST=1]
[*]Describe the error. Post its contents on this thread.
[*]At what step does the error occur?
[/LIST]
> …The website for the download is [https://osdoc.cogsci.nl/3.2/download/#ubuntu](https://osdoc.cogsci.nl/3.2/download/#ubuntu) and I believe I have Xenial.
To check version, post output of:```
lsb-release -a
```

---

### Post by TheFu on 2019-03-04
Chromebooks don't run Ubuntu stuff last time I checked.

Depending on the model, you can wipe ChromeOS, replace the firmware, void the warranty, and load Ubuntu, but this is extremely specific to the exact model of chromebook that you have.  After doing this, chromeOS will NEVER, EVER, EVER, run on the device again. I've done it with 2 chromebooks and it always required modifying the hardware which prevents chromeOS from ever working again. I suspect you don't want to do that.

There are non-ChromeOS options which can work with other OSes using virtual machines. Very few Chromebooks can support that, though both models that I have do. I was very, very careful to buy these specific models for just that purpose.  One of the chromeOS replacement is called, CloudReady.  I've not used it, but know a few people who love, love, love it. They've installed it on older laptops.

Maybe if you explain in more detail how you setup ubuntu, and the specific version, someone might be able to help?  Downloading an ISO most definitely is not sufficient.

Regardless, I suspect we can help.  I'll assume you want to keep ChromeOS, not void the warranty or even open the case for now. Please confirm.

---

