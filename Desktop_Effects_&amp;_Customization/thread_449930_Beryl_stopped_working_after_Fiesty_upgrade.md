---
title: "Beryl stopped working after Fiesty upgrade"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by zhinker on 2007-05-20
Hi, I just upgraded my system from Edgy to Fiesty.  The program's running, I see the red diamond in the corner of my screen, and when I go to the settings all the effects I want are enabled, but they don't work for some reason. (Everything else seems to be working fine)

Something that might help:  When I restarted my pc after the upgrade I got this notice saying something about proprietary drivers being used.  I didn't pay too much attention to it (like I should have) so I can't give you too much detail except there was one driver which seemed to be an ATI driver which seemed to have been enabled and some other driver which looked like it was disabled (they both had a checkmark next to the name so I'm not 100% sure)

I'm using an ATI Radeon X600 video card, if that helps.

---

### Post by tenmoi on 2007-05-20
> **zhinker said:**
> Hi, I just upgraded my system from Edgy to Fiesty.  The program's running, I see the red diamond in the corner of my screen, and when I go to the settings all the effects I want are enabled, but they don't work for some reason. (Everything else seems to be working fine)

Something that might help:  When I restarted my pc after the upgrade I got this notice saying something about proprietary drivers being used.  I didn't pay too much attention to it (like I should have) so I can't give you too much detail except there was one driver which seemed to be an ATI driver which seemed to have been enabled and some other driver which looked like it was disabled (they both had a checkmark next to the name so I'm not 100% sure)

I'm using an ATI Radeon X600 video card, if that helps.

To the best of my knowledge, you should not use the proprietary driver. Beryl just does not like it I think. B/c I once installed it on my Mobility Radeo 7500 after Beryl had been up and running, and only to mess beryl up. I uninstalled the propriety driver and things were back to normal.

to uninstall it you go to sypnatics and search for fglrx, then uninstall everything which is *fglrx*. Search for ati and install the *3daccel*. I am not so sure for mine is Kubuntu Feisty. but that was what I did to bring Beryl back to normal after an installation of the closed source driver.

Hope this helps

---

### Post by zhinker on 2007-05-20
Thanks for your reply but I already managed to get it to work.  After finding an alternate beryl install method [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") I uninstalled and reinstalled beryl and now it works like a charm (with fglrx).

Thanks anyways!

---

