---
title: "Something went wrong after upgrading to 9.04"
date: 2009-05-06
forum: General Help
---

### Post by chickentaco on 2009-05-06
When I had 8.10, I had to change my Xorg file so that I could get it to run on my native resolution.  It was working perfectly well after I changed the file.  But after I Upgraded to 9.04, the 1440 x 900 doesn't work anymore.  I still get the option to change it to 1440 x 900.  But I keep getting this message "Could not set the configuration for CRTC 321" whenever I click Apply.

If it helps solve my problem, I'm running the AMD64 version of Ubuntu, a Geforce 9400GT, and my monitor is an Acer AL1916W.

---

### Post by kpkeerthi on 2009-05-06
Revert xorg.conf to the state it was before. Restart X. Then try changing the resolution using
```
gksudo nvidia-settings
```

---

