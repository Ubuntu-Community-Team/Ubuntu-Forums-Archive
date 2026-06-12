---
title: "Freezing problem."
date: 2006-06-11
forum: Desktop Environments
---

### Post by nn04 on 2006-06-11
(sorry about the grammar, dont know when it will happen again)Glad to be on the forums btw. Hi, im having a small problem with my computer, it seems to freeze at any given point, sometimes ill be installing program in terminal, sometimes ill be surfing the web, it happens most often when im using memory/processor intensive programs (frostwire, java programs, etc...) i have a new cpu cooler, new northbridge cooler, new hard drive, 1 year old memory (mushkin) and 1 year old motherboard (ABIT - AI7), before i switched to ubuntu this would happen with my micro$oft windows xp install too, only when using graphics intensive apps (games etc...) after reformatting but before installing ubuntu i switched my graphics card to an old but gauranteed working 9500 radeon (linux drivers not yet installed) i was wondering if any of you had this problem, any any tips to fix it.
Also I was wondering, im using dapper drake (6.06) does it come with a memtest utilty? and if it does, i seem to be barred from adding system tools to my application menu, any tips on that? any help here would be greatly appreciated, thanks for looking in any case. btw this is in x interface in case u need to know.

ABIT AI7 MB
Pentium 4 3GHz
512MB Mushkin DDR400
160GB Generic HD
Generic DVD-RW
ASPIRE 550W PSU
Intel 865PE / ICH5-R Chipset

If i forgot anything else, let me know and ill fill u in, like i said, any help is appreciated.

---

### Post by rubinstein on 2006-06-11
An option for a memtest is on the grub boot manager screen; maybe you have to hit ESC to see the menu.

You can also download a Test-CD at [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/) ,  there are many diagnostic tools on that CD.

Try conservative settings in your BIOS (e.g., try to lower your processor speed, your FSB etc.)

---

### Post by tronica on 2006-06-11
just a suggestion, i see you have a P4 and i'm sure it has HT i would get the smp kernel that will help with cpu intensive apps.

I'm pretty sure this is the right command

> sudo apt-get install linux-686-smp

---

### Post by nn04 on 2006-06-11
hmmm, havent ran memtest but i installed that package, everything seems fine for now, any other ideas of what it could be? also, in my applications menu system tools is not present and i cant figure out how to make it visible, any help on that is appreciated.


edit: package install didnt work, froze up 5 mins later, ran memtest for 6 hours while i was at work, still running when i got home, no errors. only other thing is cpu right?

---

### Post by nn04 on 2006-06-14
*bump* ive switched back to badger for now, doesnt anyone have any ideas towards this? i did notice tho, while i was reinstalling badger it froze when it was autoconfiguring my network adapter (1 of 2) i disabled it, and ran the setup with the other one and everything was fine, would the freezing be caused by just a faulty network card?

---

### Post by nmehsr on 2006-06-14
i'm having this exact same problem, my comp is a bit older w/ no HTT.  It'll just stop in the middle of some random event such as moving a  window to the next workstation. It'll freeze up completely, except for the audio which'll keep going

*edit* tried memtest86 no errors appeared

---

### Post by theboomboomcars on 2006-06-14
Does the keyboard and mouse freeze, just the keyboard, or just the mouse?

---

### Post by nmehsr on 2006-06-14
The mouse continues to work, i'm not sure about the keyboard because i've never been in an app where i can type when it freezes

---

### Post by nn04 on 2006-06-15
keyboard and mouse freeze up, no ctrl alt backspace, no clicks, nothing, switched back to breezy, updated to dapper, 15 mins after restart, froze again, now ive just switched back to breezy for now, until someone figures this out, i lack experience in code to figure this out for myself, and it being completely random, i would have no idea where to start.

---

### Post by TheFifth on 2006-06-16
I've also had this problem, although since I disabled XGL and Compiz it has not seemed to happen again (Touch Wood!).

I've gone four days now without a lock up, where before it was 2-3 times a day.   Not sure if you guys are running compiz, but you might want to try going back to normal Xorg and Metacity and see if it helps.

---

### Post by ekici on 2006-06-16
I have the same freezing problem as well and just because of that I am using Breezy for the time being. The freezing happens quite often and right after start of dapper. **"TheFifth",** how can I disable XGL and Compiz on the command prompt? That is the only way I can use dapper.

---

### Post by TheFifth on 2006-06-16
Were you using XGL and Compiz?  You would have had to jump through a few hoops to enable them, so if you haven't then you weren't using them.  Basically you have to do the same process in reverse to disable them.

You'll need to edit your 'Xorg.conf' to remove anything you added there and also your 'gdm.conf-custom' to remove the lines added there.  The exact steps will vary dependent on how you installed Compiz and XGL.  There are so many different guides on here that vary dependent on your hardware, so you'll need to work out which one you used to install XGL/Compiz and follow the steps in reverse.

You can edit the config files on the command line using vim.  I'm not a vim expert and normally end up swearing at it whilst trying to use it!  You may want to type:

```
man vim
```

at the command prompt and read the man pages before attempting to edit any important configuration files with it!

Good Luck!

---

