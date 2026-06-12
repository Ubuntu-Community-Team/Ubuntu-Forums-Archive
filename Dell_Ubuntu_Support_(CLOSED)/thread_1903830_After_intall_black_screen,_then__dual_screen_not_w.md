---
title: "After intall black screen, then  dual screen not working"
date: 2012-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by benjrameur on 2012-01-03
Hello,

Computer: dell Optiplex GX 270, video card Nvidia p117

I've upgraded from 10.04 to 11.11, the install went well ...  but at restart i got (2) black screens one of them saying no signal, the other nothing. 

with 10.04, the dual screen was working great for me.

So i've push the on off button untill the computer sut down , and restarte, this time i've noticed that i have the orangy-pupulish ubuntu screen for a while, but then it turns off.
After googling for a while i've found that i need to push shift at start untill the grub appears, type "e" find the line saying quiet splash, and replace these words by nomodeset, and finally "ctrl X" . also it says to get the proprietary driver .
It worked, somewhat, both  of the screens stayed on and the computer stated, i loged on and found the additional drivers, found that ubuntu already loaded the proprietary driver, reinstalled some of the addintional software i need, updated the computer and restarted.
At restard it worked, i went to the nvidia setting to try to set the dual screen as i wanted, found that there is nothing there about it, got frustrated, unabled the nvidia controls, restarted the computer. 
At restart both of the screen worked untill right befor the login screen, then i just had one screen. I reenabled the nvidia driver, re-started ,  still one screen only ....

Should i just re-intall 10.04 ? :confused::confused::confused::confused::confused:
or there is a solution ? (i want the dual screen not to be mirror, and one oth then oriented as portrait).


Thank you.

---

