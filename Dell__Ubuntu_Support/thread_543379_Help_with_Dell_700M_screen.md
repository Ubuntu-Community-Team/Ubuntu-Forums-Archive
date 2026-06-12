---
title: "Help with Dell 700M screen"
date: 2007-09-05
forum: Dell  Ubuntu Support
---

### Post by sRsGreen on 2007-09-05
Hello,

I am new to linux. i recently moved from win xp to ubuntu. After installing ubuntu on my dell 700m laptop it does not take up all the screen, instead it leaves about an inch space on either side of the wide  screen. Can some one please help me correct this? thank you.

---

### Post by technikalKP on 2007-09-05
Try installing the 915Resolution fix for the Intel video chipset:

go to system->administration->synaptic package manager, find the '915Resolution' item and select it for install.  Restart and see if that helps.

I know I had to do this to get proper resolution on my 700m, but I don't remember have an blank border around the screen...  Could be that you have your BIOS set up to not stretch the display - which would result in a border without the 915 fix in place since it would be displaying at something other than the 1280x800 native resolution of the screen.

---

### Post by sRsGreen on 2007-09-05
technikalKP,

Thank you, it worked, now ubuntu takes up all the screen.

---

### Post by vatsu on 2007-09-15
[QUOTE=technikalKP;3313615]Try installing the 915Resolution fix for the Intel video chipset:

I did exactly this on my 700m and to my horror I could not get anything on my screen. I could not restore to my earlier configuration and being new to Linux, it as a complete mess, I have now re-installed Ubuntu but .. though I wish to fix the resolution, I am fearful. Can you help?

---

### Post by technikalKP on 2007-10-05
I'm not sure what to tell you.  I just installed the 915Resolution package from the Synaptics Package manager and everything worked.  No need for any other tweaking...  I'm not sure what would have caused your issue.  I don't believe the 700m had any optional video cards, so all of them should be Intel based and should work with the standard 915 fix.  

Sorry I can be of more help...

---

