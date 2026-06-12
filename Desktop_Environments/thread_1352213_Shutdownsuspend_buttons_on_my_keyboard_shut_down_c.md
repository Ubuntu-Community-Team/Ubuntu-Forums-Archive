---
title: "Shutdown/suspend buttons on my keyboard shut down computer without warning"
date: 2009-12-11
forum: Desktop Environments
---

### Post by maciekmn on 2009-12-11
My new keyboard has shutdown/suspend etc buttons which are extremely annoying..

They are located right above arrows / below the 'delete / end / page down' keys..
so they are extremely easy to press by mistake.. and when I do.. computer shuts down / or goes to sleep.. I have to press power button to wake it up seems like.. 
But then it goes through the 'corrupted filesystem' messages and scan.. 

so.. whenever I press the button by mistake I loose 15 mintues of restarting and scanning filesystem.. I just changed it yeasterday and that's how long I could cope with it before scraming for help here!!!

OK.. on keyboard shortcuts preferences window I found out the power button is listed as:
x86poweroff

The button could be ok.. if it asked me for confirmation.. and do proper shutdown..


Please help..

---

### Post by akashiraffee on 2009-12-11
What kind of keyboard is that?  Lemme make a mental note not to get one...;)

---

### Post by maciekmn on 2009-12-11
First little update: 
The keyboard's power button actually functions properly: it does what Ctrl-Alt-Del default behavior does: shutdown menu.

The sleep button is the problem (X86sleep). It gives no warning and puts my system to unrecoverable sleep mode.. my power light flashes and the keybaords 'wake up' button or any buttons or mouse won't bring it back.. just the power button, which just restarts the computer and puts the drive in 'dirty' mode..

I just tried this:
1. I did check CMOS setup and there's no power options menu, but AHCI setting were all turned off. (so no remedy there)

2. I went to Power Management and changed the 'When the suspend button is pressed' to 'Do nothing' (there is no ask option for that)
I will wait until I want to turn off the computer (or until I press that button by mistage again) to see if that worked (crossing my fingers)



Answering what keyboard it is:

It's some generic cheapy keyboard that I got in microcenter: Inland.. well.. this was the nicest one of the cheapy keyboards.. It actually looks and feels solid (that's why I decided to give it a try and bought it). I liked the layout on it with all the standard keys in right places (My last keyboard bothered me because it had Print screen / scroll lock / pause-break just right to the backspace key and in ubuntu I kept pressing print-screen button by mistake.

Still, the print-screen window popping out was JUST A BIT LESS annoying than my computer going to sleep and going through disk check)

---

### Post by maciekmn on 2009-12-13
OK.. the last think I did fixed it:

Under 'Power Management' I changed the 'When the suspend button is pressed' to 'Do nothing'

---

