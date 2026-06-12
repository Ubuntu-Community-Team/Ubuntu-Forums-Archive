---
title: "WOW crashes after an hour of playing, help..."
date: 2007-01-28
forum: Gaming &amp; Leisure
---

### Post by sir_fragalot on 2007-01-28
Ok I am running World of Warcraft on my laptop which has a mobility radeon 9700. So when I load up WOW, it running perfectly like windows would. After about an hour it gets slow as hell and crashes and the only thing I could do is hold in the power button to completly shut the computer off. The only other thing I have going is banshee music player and maybe firefox to look at quest data and stuff, thats it. I run wow in open gl on 1280 x 800 because thats whats my monitor is at. So anyway can anyone help me possibly fix my problem, I am running Edgy and my wine is set to emulate windows 2000. 

Thanks

---

### Post by Sammi on 2007-01-28
It's very hard to help people with ATI cards. Some errors are very random and mysterious and may be way beyond what the users here on ubuntuforums are able to help you with :(

Check for video driver updates or even just try to reinstall your video driver.

Also be sure you've tried everything in the three major sources of info on WoW/Wine:
 * [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
 * [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)
 * [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

Especially the last one may be where the real WoW/Wine specialists hang out, so i think you should try your problem there.

---

### Post by Ferrat on 2007-01-29
> **sir_fragalot said:**
> Ok I am running World of Warcraft on my laptop which has a mobility radeon 9700. So when I load up WOW, it running perfectly like windows would. After about an hour it gets slow as hell and crashes and the only thing I could do is hold in the power button to completly shut the computer off. The only other thing I have going is banshee music player and maybe firefox to look at quest data and stuff, thats it. I run wow in open gl on 1280 x 800 because thats whats my monitor is at. So anyway can anyone help me possibly fix my problem, I am running Edgy and my wine is set to emulate windows 2000. 

Thanks

If it gets slowed then crashes, then it sounds like a flood problem, some memory not clearing right , hard to say what memory tho but if the whole computer lags then my guess would be the RAM, but if not (when tabed out) then it's the V-RAM 

Try running using WinXP emulation instead.

---

### Post by Sammi on 2007-01-29
You can change between the different emulation modes in the configuration window, that you get by running this command: winecfg

You should try a few different modes, especially win2k, winXP, and win98

---

