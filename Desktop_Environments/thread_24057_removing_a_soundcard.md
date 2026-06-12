---
title: "removing a soundcard"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Hinko on 2005-04-05
Hi, I just moved from SuSe to Kubuntu (been going from Suse to Ubuntu, to Yoper, back to Suse and now Kubuntu for over a month but this time Kubuntu is here to stay)

And I was actually wondering if there is perhaps any way to remove or deselect one of my soundcards. I allways Used Yast for that in SuSe, and the thing is, I need to configure my audio right. I can see in Ksysguard that both my soundcards are working fine, and are being recognised, now I just want to remove the one stuck to my main-board. Any thoughts?

---

### Post by cwaldbieser on 2005-04-05
I had the same kind of problem.  Someone recommended that maybe I could turn off the built in card from BIOS.  Maybe that is your answer?

I was not really keen on doing that since I still have a dual-boot box where the other OS uses the built in card.  I ended up just configuring esd, SDL, openAL, etc. to use the second card.

Hope that helps!

---

### Post by Hinko on 2005-04-05
nope, not possible in my BIOS :-( 

Besides, I just want to be able to do it anyway.... This should be easy, right?

---

