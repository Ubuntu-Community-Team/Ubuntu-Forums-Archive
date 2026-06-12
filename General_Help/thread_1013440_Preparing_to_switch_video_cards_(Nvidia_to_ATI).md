---
title: "Preparing to switch video cards (Nvidia to ATI)"
date: 2008-12-16
forum: General Help
---

### Post by RFXCasey on 2008-12-16
Ok, here's the deal. I just bought a new ASUS ATI 4830 PCIE card from newegg that I will be replacing my old Geforce 6800 AGP card with. Before you ask, I have a ASRock 939dualSATA2 motherboard that has both AGP and PCIE x16 expansion slots. I was tempted to buy a 9800 GT because I hear the support for Nvidia is better as far as Ubuntu is concerned, but since I am going to be dual booting XP for gaming I just couldn't resist getting the ATI card based on the reviews I have read, not to mention the price, $120 bucks. I'm running Hardy and don't wanna have to reinstall Linux to get this working. What do I need to do to make the changeover go the smoothest possible? I am currently not using envy if that makes a difference. What I would really like to avoid is the Black Screen of Death although I do have other machines for interwebbing recovery proceedures just in case. I'm not very good with the command prompt as far as Linux is concerned. I have also read that ATI doesn't support twinview in Linux. Is this true?

---

### Post by damis648 on 2008-12-16
I can't tell you much about ATI, I primarily use nVidia cards, so I cannot tell you if twinview will work. As far as installation goes, I would go about it in the following way: First, disable the proprietary nVidia driver via System>Administration>Hardware Drivers. Then shut down and install the new card. If boot into Ubuntu. If it boots fine, then just go ahead to enable the new restricted driver for the ATI card; if not, then boot into recovery mode and choose the 'xfix' option, and that should do it. Then resume normal boot.
Cheers!:popcorn:

---

### Post by RFXCasey on 2008-12-16
Thanks, that makes perfect sense. I will try it as soon as I get home from work tonight and let you know how it turns out. The UPS guy just dropped off the card before I left today so hopefully I will be seeing all the pretty colors tonight when I hook it up. I think my first Ubuntu test will be with Nexiuz. Hopefully I can max out everything at 1650x1080. I hope to be pleasently supprised [-o< as the 4830 should be quite a major leap from my 6800 although that was a great card for playing games. Both cards are 256 bit, I wouldn't settle for at least that.

---

