---
title: "APT partial is missing"
date: 2006-01-08
forum: General Help
---

### Post by siucdude on 2006-01-08
Hey I don't know what I did but i get the following error after i installed some new stuff. I have tried synaptic and apt-get from terminal same error. Plus I went into kde and tried adept but that program just crashes all the time. thank you in advance.

***E: Archive directory /var/cache/apt/archives/partial is missing.***

---

### Post by GeneralZod on 2006-01-08
Never heard of that one before, but try:

```

cd /var/cache/apt/archives/
sudo mkdir partial

```

---

### Post by siucdude on 2006-01-08
thanks that worked

---

