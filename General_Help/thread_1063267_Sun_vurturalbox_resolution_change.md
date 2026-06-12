---
title: "Sun vurturalbox resolution change?"
date: 2009-02-07
forum: General Help
---

### Post by Kain000 on 2009-02-07
Does anyone know how to change the screen size in a virtural machine inside virturalbox?    

I've got kubuntu in a virtural machine but the resolution is way down and I cant even see the entire desktop.

I remember in a windows VM you needed to install "virturalbox extras" but I'm not sure what to do for a ubuntu VM.

---

### Post by zero777zero on 2009-02-07
should be able to change it from inside the virtual OS itself, not a setting on virtual box.

system->preferences->screen resolution

---

### Post by howefield on 2009-02-07
> **Kain000 said:**
> Does anyone know how to change the screen size in a virtural machine inside virturalbox? 

I remember in a windows VM you needed to install "virturalbox extras" but I'm not sure what to do for a ubuntu VM.

Installing guest additions is a good idea, it will give you better drivers which will aloow you a greater choice of resolution plus some other benefits.

From the devices menu of the virtualbox window, select Install Guest Additions.

---

