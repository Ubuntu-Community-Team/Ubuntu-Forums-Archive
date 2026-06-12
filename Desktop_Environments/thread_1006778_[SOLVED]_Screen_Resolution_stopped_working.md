---
title: "[SOLVED] Screen Resolution stopped working"
date: 2008-12-09
forum: Desktop Environments
---

### Post by seanlano on 2008-12-09
Hello.
I am a novice user of Ubuntu, but I am slowly becoming more proficient in it's use. Basically, I love Ubuntu. But I am currently having a problem: 

I have a Thinkpad R61i with 8.10 on it. I managed to get it all working almost flawlessly (except for built in card reader) and it worked fine for many months. However, yesterday I plugged the VGA output into a projector, and then went to the Screen Resolution program. I set the output to mirror the laptop screen, with the resolution set to 1024x768 (the projector was not widescreen like my laptop) and initially it did not work. I had to enter my password to authorise some sort of change (I don't recall what it was), then Ubuntu forced me to log out and back in again. After that the projector did not work still, so I decided to just go back to normal. **So here is my problem:** I cannot select the native 1280x800 resolution for my screen anymore!!! It is just gone from the list! So, please, what do I do now? I guess I need to reset some sort of config file to revert to the out-of-the-box settings, but which one? 

Thanks in advance.

P.S. I did eventually get the projector working, so at least I didn't just ruin my resolution for nothing.

---

### Post by seanlano on 2008-12-10
I figure it was some sort of config file, so by trial-and-error I backed-up and deleted the .config, .gnome2, .metacity etc. folders, then re-introduced them (and in the process accidentally screwing up my entire home folder permissions, which took while longer to fix by struggling with chmod). 


I isolated the problem to the file */home/sean/.config/monitors.xml*. I deleted this file and all was fixed. The file has not been auto-replaced yet by whatever program created it, but it doesn't seems to matter.

---

