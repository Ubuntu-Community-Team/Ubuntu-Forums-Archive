---
title: "Environment variables"
date: 2006-06-19
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-19
Hi All,


I am setting MOZ_ENABLE_PANGO environment in ".bash_profile". I added 2 extra lines as sshown below in ".bash_profile". 

MOZ_ENABLE_PANGO=1
export MOZ_ENABLE_PANGO 

I restarted the computer when I entered echo $MOZ_ENABLE_PANGO  nothing showup. Is that variable set or not?

Regards,

Swaroop.

---

### Post by xslf on 2006-06-30
I think it's actually
MOZ_DISABLE_PANGO=0

---

