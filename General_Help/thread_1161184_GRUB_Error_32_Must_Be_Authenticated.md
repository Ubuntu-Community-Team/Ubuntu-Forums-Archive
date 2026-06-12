---
title: "GRUB Error 32: Must Be Authenticated"
date: 2009-05-16
forum: General Help
---

### Post by Serpher on 2009-05-16
So I tried to get Virtual Box-ose running, and when trying to boot up Windows XP, it gave me an error telling me to install some sort of package. I went into terminal to apt-get it and it just gave me a list of choices. I picked the one at the top as it seemed like the most recent version and it installed fine. It said that I had to do a system restart for the changes to take effect so I did. I now have an additional GRUB boot up which is some sort of virtual boot up. When I select it I get

Error 32: Must be Authenticated

Sadly, for my other 2 boot options, do the same thing, both Ubuntu 8.04, one of them not working properly with my video driver. So I'm now booted up in Windows. Can somebody please give me a hand, I also have no knowledge of the syntax GRUB uses in the initframs box so if it involves that please speak to me as if I'm retarded.

---

### Post by nolliecrooked on 2009-05-16
> **Serpher said:**
> So I tried to get Virtual Box-ose running, and when trying to boot up Windows XP, it gave me an error telling me to install some sort of package. I went into terminal to apt-get it and it just gave me a list of choices. I picked the one at the top as it seemed like the most recent version and it installed fine. It said that I had to do a system restart for the changes to take effect so I did. I now have an additional GRUB boot up which is some sort of virtual boot up. When I select it I get

Error 32: Must be Authenticated

Sadly, for my other 2 boot options, do the same thing, both Ubuntu 8.04, one of them not working properly with my video driver. So I'm now booted up in Windows. Can somebody please give me a hand, I also have no knowledge of the syntax GRUB uses in the initframs box so if it involves that please speak to me as if I'm retarded.

Did you install Windows xp on the same virtual hdd image as 8.04 or something?

---

### Post by Serpher on 2009-05-16
> **nolliecrooked said:**
> Did you install Windows xp on the same virtual hdd image as 8.04 or something?

I can't quite recall, but my computer was working fine after trying to configure it all. I think when allotting Hardrive space I just used the same partition I was in I would guess.

---

### Post by nolliecrooked on 2009-05-16
> **Serpher said:**
> I can't quite recall, but my computer was working fine after trying to configure it all. I think when allotting Hardrive space I just used the same partition I was in I would guess.

does the pc fail to boot, or just in virtualbox?

---

### Post by Serpher on 2009-05-16
> **nolliecrooked said:**
> does the pc fail to boot, or just something in virtualbox?

When I boot my computer up, when I get to GRUB, and select any of my Ubuntu boot options, it gives me this error. Windows XP still boots up fine which is the only one in a separate partition.

---

### Post by nolliecrooked on 2009-05-16
> **Serpher said:**
> When I boot my computer up, when I get to GRUB, and select any of my Ubuntu boot options, it gives me this error. Windows XP still boots up fine which is the only one in a separate partition.

its actually pretty easy to fix grub, but ive never seen that before, so maybe it needs more than config'in...

---

### Post by Serpher on 2009-05-16
> **nolliecrooked said:**
> ok its actually pretty easy to fix grub, but ive never seen that before, so maybe it needs more than config'in...

What does somebody usually mess around with to fix GRUB with then?

---

### Post by nolliecrooked on 2009-05-16
> **Serpher said:**
> What does somebody usually mess around with to fix GRUB with then?

the livecd

---

### Post by Serpher on 2009-05-16
> **nolliecrooked said:**
> the livecd

I assume this would be done from terminal then? What would you suggest I do in there? I have like no knowledge about GRUB.

---

### Post by nolliecrooked on 2009-05-16
> **Serpher said:**
> I assume this would be done from terminal then? What would you suggest I do in there? I have like no knowledge about GRUB.
 
i added you on msn, ill try and explain there

---

