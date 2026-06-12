---
title: "computer freezes when it loads the desktop"
date: 2010-01-05
forum: Desktop Environments
---

### Post by wcutrombonekid on 2010-01-05
so, i installed new ram in my computer today (4 gigs, hells yeah) anyway, computer was running absolutly famously, i was playing with compiz since i now have the power to spare to run all this fun stuff. i was following a video on youtube about getting the cube and checked "reflection" and my computer immediately froze, now everytime i turn on my computer and go to my ubuntu partition, i lets me log in and plays the startup sound but then freezes. 
 
i guess clicking on reflection did it, but how do i undo it when i can't get into my computer?

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> so, i installed new ram in my computer today (4 gigs, hells yeah) anyway, computer was running absolutly famously, i was playing with compiz since i now have the power to spare to run all this fun stuff. i was following a video on youtube about getting the cube and checked "reflection" and my computer immediately froze, now everytime i turn on my computer and go to my ubuntu partition, i lets me log in and plays the startup sound but then freezes. 
 
i guess clicking on reflection did it, but how do i undo it when i can't get into my computer?

Take out the o new pieces of ram and see if everything is back to normal. If it is, RMA your ram and get two new sticks.  This happens quite frequently on my builds, getting 4 sticks of ram and 1 or two being bad and I have to return them.  Exactly what you are reporting is the behavior I see

---

### Post by wcutrombonekid on 2010-01-05
i guess i'll try that, the thing is i'm using my vista partition right now and its working fine. and it had been working fine for about 5 hours before that.  it wasn't immediate

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> i guess i'll try that, the thing is i'm using my vista partition right now and its working fine.

It may not be the issue, but it is a start.  Process of elimination and an effort to get back to Ubuntu

---

### Post by wcutrombonekid on 2010-01-05
ok, i'll post back in a few minutes

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> ok, i'll post back in a few minutes

If it is still doing the same thing, put the memory back in and do the following


if you can press ctrl+alt+f1 after the desktop freezes, then try:
sudo killall -9 compiz* 

if not, you will need to boot into term mode to do the following

Otherwise, remove compiz, purge the configure files, and reinstall:
sudo apt-get remove --purge compiz*

---

### Post by wcutrombonekid on 2010-01-05
ctrl alt f1 just opens the terminal right?

i'll give it a try, the ram wasn't it, it still did it

---

### Post by wcutrombonekid on 2010-01-05
also, when you say "term mode", do you mean recovery mode?

---

### Post by wcutrombonekid on 2010-01-05
sweet, that worked.  i'm back in action.

what i don't understand is how clicking on "reflection" would make it do that

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> sweet, that worked.  i'm back in action.

what i don't understand is how clicking on "reflection" would make it do that

Glad you got it back!

I would say it has more to do with your video card or driver.  What card do you have and what drivers loaded?

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> sweet, that worked.  i'm back in action.

what i don't understand is how clicking on "reflection" would make it do that

Which worked, 1st option or 2nd?

---

### Post by wcutrombonekid on 2010-01-05
> **VastOne said:**
> Glad you got it back!

I would say it has more to do with your video card or driver.  What card do you have and what drivers loaded?

i think its an intel X3100

its just a crappy integrated video card, whatever it is

and i checked and i have no drivers loaded

---

### Post by wcutrombonekid on 2010-01-05
> **VastOne said:**
> Which worked, 1st option or 2nd?

the second one, it didn't even load the desktop, it sat at the "ubuntu" loading screen, so i had to go into recovery mode

---

### Post by VastOne on 2010-01-05
> **wcutrombonekid said:**
> i think its an intel X3100

its just a crappy integrated video card, whatever it is

and i checked and i have no drivers loaded

OK, before you loaded compiz, did you try System Preference Appearance and try the Visual Effects and change it to a high setting? and if you did, what was the result?

Edit 

I ask this because you have to have at least a Normal or High level of Visual Effects loaded before Compiz will work. When you try to change to a higher level in Visual Effects it will then try to load the necessary drivers.

---

### Post by wcutrombonekid on 2010-01-05
i think it was on none, but i changed it to high and then had already made a few changes that all were working quite fluidly.  this is why it confuses me as to this one specifically.


so after i purged it, i wanted to mess with it, so i redownloaded it and now whenever i turn my computer on anything but none, it lags like a mofo and in my system monitor it shows something like "compiz real" as using like 80% of my processor!  it wasn't doing this before, what happened?

---

### Post by VastOne on 2010-01-06
> **wcutrombonekid said:**
> i think it was on none, but i changed it to high and then had already made a few changes that all were working quite fluidly.  this is why it confuses me as to this one specifically.


so after i purged it, i wanted to mess with it, so i redownloaded it and now whenever i turn my computer on anything but none, it lags like a mofo and in my system monitor it shows something like "compiz real" as using like 80% of my processor!  it wasn't doing this before, what happened?

This is the issue with onboard video and shared memory/processes.  It looks like candy but it sure doesn't taste like candy!

Compiz is most likely a no go on this system.

---

### Post by wcutrombonekid on 2010-01-06
sad day, well, thanks for your help, i appreciate it.

---

