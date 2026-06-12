---
title: "hiii .."
date: 2009-01-18
forum: General Help
---

### Post by me.translucent on 2009-01-18
can't see the c drive .. guys i installed wubi but i can't see my c drive inside it :( is there any work around so that i can use my c drive i have all my data in c drive only :(****

---

### Post by Yashiro on 2009-01-19
If you're running from your Wubi Ubuntu install your Windows drive is called /host.

---

### Post by Feivel on 2009-01-19
> **Yashiro said:**
> If you're running from your Wubi Ubuntu install your Windows drive is called /host.

It is? On my Wubi install my Windows C:\ drive showed under /media as ACER.

ETA - OP, go to your filesystem/media directory and open the folder for your C:\ drive, it will show with it's volume label.

---

### Post by brandon88tube on 2009-01-20
> **Feivel said:**
> It is? On my Wubi install my Windows C:\ drive showed under /media as ACER.

ETA - OP, go to your filesystem/media directory and open the folder for your C:\ drive, it will show with it's volume label.

Do you by any chance have multiple drives or ubuntu installed on another drive?

---

### Post by Feivel on 2009-01-20
> **brandon88tube said:**
> Do you by any chance have multiple drives or ubuntu installed on another drive?

Who me or the OP?

---

### Post by brandon88tube on 2009-01-20
You, I wanted to know because I've never had it come up how you described.

---

### Post by Feivel on 2009-01-20
> **brandon88tube said:**
> You, I wanted to know because I've never had it come up how you described.

Ubuntu was on my Acer drive. It shows as a folder. Are you saying your HD doesn't show up under /media?

---

### Post by brandon88tube on 2009-01-22
What I am saying is that under /media there is only cdrom,cdrom0 and disk. disk being my second hard drive and not the one ubuntu is installed on. The only way to get to that is through /host.

---

### Post by me.translucent on 2009-02-03
> **Yashiro said:**
> If you're running from your Wubi Ubuntu install your Windows drive is called /host.

yeah .. i got it .. it was under /host .. thanx every one .

---

