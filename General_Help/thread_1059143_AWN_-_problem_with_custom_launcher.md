---
title: "AWN - problem with custom launcher"
date: 2009-02-03
forum: General Help
---

### Post by VitaminCPP on 2009-02-03
I have added a launcher for my home directory, just a simple launcher which invokes "nautilus". When I turn on my computer, the launcher doesn't work, i.e. the icon is jumping (the effect for mouse hover), but when I click on it, nothing happens. When I restart AWN (close and launch again manually), everything works. How can I fix it, so I don't restart AWN each reboot?

Thanks for your attention and sorry for my English mistakes. ;-)

---

### Post by Brightbelt on 2009-02-03
HI,
  I just went through learning this. Firstly, you need to make sure that the programs 'Compiz' and 'Fusion Icon' are installed. Check for these through the Synaptic Package Manager. These are necessary for AWN to work correctly. 

Btw, I also suggest installing AWN through Synaptic in the first place and Not Add/Remove. I think it's just a more solid install. 

Then, you need to set up all these programs (fusion-icon, compiz and AWN) to start at boot up. Do this through the System/Preferences/Sessions menu. 

It doesn't so much matter what you enter for the descriptions but use these for the commands:
avant-window-navigator ...(with the hyphens), fusion-icon and compiz.

This should get things to start automatically when your desktop loads up.

---

### Post by VitaminCPP on 2009-02-04
Thank you for your answer. I didn't have Fusion Icon before, which I installed. I also didn't have compiz in my sessions because I had thought it starts automatically. So I added it. But it didn't fix my problem, still the homepage icon doesn't work from the beginning. =\

---

