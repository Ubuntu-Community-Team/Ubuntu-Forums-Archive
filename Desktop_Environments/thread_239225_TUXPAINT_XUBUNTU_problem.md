---
title: "TUXPAINT XUBUNTU problem"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Efrain Valles on 2006-08-18
Dear Friends:

I recently isntalled xunbuntu on my very old pentium III 450... I  set it up for my daughter to use t as her first PC... I intalled TUXPAINT... the first Three days it ran great. but now whne Itry to run it ... it doesn't do a thing... I run on terminal and It reads 

[COLOR="Red"]valles@hal:~$ tuxpaint

You're already running a copy of Tux Paint!

valles@hal:~$
[/COLOR]
How can this be... I just booted and I am sur I didn't run it...

I have trid reinstalling it... deleting it and reinstalling it from scratch... I have tried everything a user would do...

what can be wrong... (other games run great... tuxtyping... tuxmath etc...

thanx  guys

---

### Post by Markus Valkeapaa on 2006-08-19
Does ```
ps -au username
``` list tuxpaint? Then maybe with 'kill' you could stop it and then run again? I know this would be just kind of first aid, not really solving the problem.
-Markus

---

### Post by Efrain Valles on 2006-08-19
it doesn't list tuxpaint.. I have tried killall tuxpaint...
but keeps prompting 
no proceses killed

I created a new user... and when I try tu run it ... it executes perfectly... 
My guess is my daughter hardlocked tuxpaint. and her session was saved some how...

Strange stuff 

on xubuntu... Tuxpaint is categorized under EMULATION in the menu... I wonder if that has to do with it... 

eff

---

### Post by Markus Valkeapaa on 2006-08-19
Strange indeed. Anyway, nice that Tuxpaint works now. It's good program. 
-Markus

---

