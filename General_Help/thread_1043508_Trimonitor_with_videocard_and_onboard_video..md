---
title: "Trimonitor with videocard and onboard video."
date: 2009-01-18
forum: General Help
---

### Post by Naddiseo on 2009-01-18
I'm trying to set up a 3rd monitor to work with. I currently have duel monitors working on my radeon HD4850 on my [M3A78-T]("http://www.asus.com/products.aspx?l1=3&l2=149&l3=731&l4=0&model=2321&modelmenu=1") and was wondering if I could use the onboard video to add a third monitor. From what I understand of the Xorg conf, I just have to add a Device section for the onboard videocard, then tell X to extend the screen onto that.

Is what I want to do even possible?

Thanks.

*Forgot to mention: using Jaunty.

---

### Post by hcaicedo on 2009-05-01
Same problem here. trying to install a third monitor in the onboard video card. No luck so far

---

### Post by Hobgoblin on 2009-05-01
Usually onboard video is disabled when an add-in card is detected.

You might be able to override this via the BIOS (though I have never seen such an option), or use a 2nd video card.

---

