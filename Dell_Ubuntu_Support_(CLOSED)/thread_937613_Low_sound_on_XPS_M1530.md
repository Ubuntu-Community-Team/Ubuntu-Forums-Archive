---
title: "Low sound on XPS M1530"
date: 2008-10-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aybara on 2008-10-04
I'm running a standard 8.04 on my XPS M1530, and all but sound works well. The sound works, but is way lower than in Vista. I have gotten debug assistance in #alsa, tried different model options and such, but nothing has worked.

I have confirmed a bug reported at [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3785](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3785), concerning this issue. Since I'm a bit hard of hearing, this is annoying, in particular when I try to use the internal speakers.

I see that M1530 is now sold with Ubuntu by Dell, so I was wondering if maybe they have a patch/fix for this in some custom packages? Anyone with this laptop or another laptop with the same codec out there? Is there a Dell-Ubuntu-ISO that I can try to install?

Other solutions are of course also welcome :-)

---

### Post by manicmario on 2009-01-17
Hi there. I also have a dell m1530 with the same problem. After reading countless pages i came along the solution totally by accident. Double click the speaker in the top right hand corner, then you'll see the mixer and you'll see the "Front" switches are a bit lower, raise those and the sound should be blasting through. Something so simple always is so hard to figure out hey :). anyways hope its not too late for this reply.

enjoy

---

### Post by Aybara on 2009-01-18
Thanks a lot for the reply, but I'm afraid I had already done that. I have made sure all sliders in alsamixer are good, but still the volume is much lower than in windows. Since I have posted I sold my XPS and bought a MacBook Pro, so now I have all the volume I want ;-)

---

### Post by vpp84 on 2009-01-19
i had same issue with my Dell Studio 15 laptop. Noting helped on sliding the sliders...

This is what helped me:
- Synaptic > Repositories > Update > Pre-Released Updates... Put a tick there adn then as usual reloadd button and if you find any updates simply dload and install it.. this solved my issue

**PS: am on Intrepid Ubuntu 8.10**
> **Aybara said:**
> Thanks a lot for the reply, but I'm afraid I had already done that. I have made sure all sliders in alsamixer are good, but still the volume is much lower than in windows. Since I have posted I sold my XPS and bought a MacBook Pro, so now I have all the volume I want ;-)

---

