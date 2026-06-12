---
title: "need help changing character encoding"
date: 2007-07-28
forum: Desktop Environments
---

### Post by isecore on 2007-07-28
Ok, so me and my girlfriend decided to get rid of the last installment of Windows here and instead formatted her machine and put Ubuntu Feisty on it.

For various reasons we need to change the character encoding from UTF-8 on her machine to ISO-8859-1.

I managed to do this on my machine, by first editing /var/lib/locales/supported.d/local (adding sv_SE ISO8859-1 since she's running Swedish language) and after that /etc/environment (changing LANG to LANG=sv_SE.ISO-8859-1). On her machine however this has no effect, despite it working fine on my own machine.

Any tips?

Also, am I the only one who think that Ubuntu needs an easier way of changing character encoding? Something along a simple little GUI utility would be nice, especially since changing languages is so darn easy.

---

### Post by Hugo Galvão on 2007-08-11
I may be wrong here, but I think that this page may be able to help you, just take a look and let me know if you worked something out with that

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

