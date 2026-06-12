---
title: "I desperate need of Help"
date: 2005-09-06
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-06
Hello,


I have a compaq 400 mhz 224 ram with ess on board sound card. I have been fighting for days trying to get the sound going and to my dismay Im not having any luck. I have read numerous posts and how tos but none of these seem to work. I really like ubuntu as a distro however just no sound any ideas?

---

### Post by skoal on 2005-09-06
Have you tried this [link](https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28soundcard%29)?

If that don't help, what does: 

lspci |grep -i "audio\|multimedia"

from a terminal return?  Do you have an ISA card, integrated on board sound?

\\//_

---

### Post by az on 2005-09-06
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by karuptdata on 2005-09-07
I do apologize to both azz and skoal i was at work trying to do 50 things at once..so i tried to follow the instructions on the old sound card page and when i did modprobe snd-es18xx it gave me the following message

sudo modprobe snd-es18xx
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.12-8-386/kernel/sound/isa/sn d-es18xx.ko): No such device
FATAL: Error running install command for snd_es18xx

---

### Post by az on 2005-09-07
Is is diabled in the bios?  Do you have another card installed?  Is plugnplay OS set (it should be set to no for linux)

Is that the correct driver?

---

### Post by skoal on 2005-09-07
Howdy,

Karupt, you have several other ESS modules you can choose from, not just the snd-es18xx driver.  Check that list on that wiki and try one of the others:

snd-es1688 (ISA)
snd-es968 (ISA, Soundblaster compat)
snd-es1938 (PCI)
snd-es1968 (PCI)

* You can't just pick any of those either.  What is returned from the lspci command I posted earlier (if you don't know exactly what type of card you have)?

\\//_

---

### Post by karuptdata on 2005-09-08
You guys rock thanks you so much im enjoying my music now as we speak..The problem was 2 things wrong driver tryin to be installed, and my cousin had disabled it in the bios just to give me a headache..Anyway SKOAL AND AZZ YOU GUYS ROCK Thanks for your patience and skills..One more thing and il leave you guys alone i swear..Ubuntu is the only distro that i now run on my network i love it...So what can i do to support the project as well as help out??

---

### Post by skoal on 2005-09-08
[QUOTE=karuptdata]...So what can i do to support the project as well as help out??[/QUOTE]
Good question.  At least for me, help those as others have helped you.  A little bit of your time helping others save some of theirs is more valuable than any change you could pull out of your pockets.  Well, forum donations are good too.  Don't get me wrong.

You can volunteer to help out with the Wiki, or just take some time here in these forums to spread some of your experience around, sharing some of your valuable insight.  I learn something new every day in these forums.  As a whole, the community grows stronger by the day as we assimilate more knowledge.  Soon, the Ubuntu Borg will be ready for victory, with Mark Shuttlekutus leading the way...

\\//_

---

### Post by karuptdata on 2005-09-08
Ok awesome lets get started....LOL Thanks guys

---

