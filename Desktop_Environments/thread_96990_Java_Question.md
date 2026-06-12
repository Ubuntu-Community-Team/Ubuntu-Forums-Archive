---
title: "Java Question"
date: 2005-11-30
forum: Desktop Environments
---

### Post by Navyblue on 2005-11-30
Hi guys,

I have j2re1.4 installed from the official repository and sun-j2re1.5 installed from Automatix.

I also have j2re1.4-mozilla-plugin installed from the official repository which depends on j2re1.4.

I only use Java for web surfing, Which version of j2re should I keep? Would sun-j2re1.5 work on Firefox if I remove both j2re1.4 and j2re1.4-mozilla-plugin?

Also what is the command/script for choosing which plugin to use? I remembered such thing exists but couldn't find where the link was anymore.

Thanks.

---

### Post by RAOF on 2005-11-30
The command for switching between installed versions of java is
```
sudo update-alternatives --config java
```
The sun 1.5JRE **should** come with a firefox plugin, so you should only need that one.  I'm not certain, however.

---

### Post by HighPlainsDrifter on 2005-11-30
```
sudo update-alternatives --config java
```

will help you switch java versions 'on the fly'.

---

### Post by HighPlainsDrifter on 2005-11-30
RAOF beat me to the answer :)

---

### Post by Navyblue on 2005-11-30
Thanks a lot guys. :)

---

