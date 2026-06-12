---
title: "Computer freezing"
date: 2009-01-05
forum: General Help
---

### Post by Jameshardy88 on 2009-01-05
hi i am running intrepid on a dual boot pc and i absolutey love ubuntu however i am having problems with my computer. Twice in the last 2 days it has frozen whilst in ubuntu, both times whilst performing non-strenuous tasks. i can't really give any more information than that really =( does anyone know what this could be, how i can try to find out, or just generally the best thing to do when in a freeze situation?

thanks for the help,

James

---

### Post by blazemore on 2009-01-05
Are you using a wireless network adaptor?

---

### Post by Jameshardy88 on 2009-01-05
erm, well i am connecting to the internet wirelessly on my laptop yes

---

### Post by blazemore on 2009-01-05
Do you know what adaptor you are using?

---

### Post by Jameshardy88 on 2009-01-05
i think it is a Broadcom 4312

---

### Post by blazemore on 2009-01-05
Alright can you answer these questions?

1) When it freezes, does anything happen when you press Ctrl+Alt+Backspace?
2) Do the num/caps/scroll lock keys work when it's frozen? Does pressing them change the status of the lights (on/off)

If the answer to these questions is no, it's probably kernel panic. I don't know how to, but if someone could say how to grab the kernel log that would be useful, is it dmesg?

---

### Post by Jameshardy88 on 2009-01-05
1) no it does nothing
2) im not sure i haven't tried it, i will do next time

sorry im still a bit of a linux newb and don't know what dmseg is. I have to linux kernel options when i boot, would booting into the alternate kernel possibly help?

---

### Post by blazemore on 2009-01-05
The alternate kernel is an old version retained from before an update.
If using this kernel stops the freezing, then use it! There are few or no differences between minor kernel versions.

As an aside, if you disable the wireless in hardware (with the switch on your laptop) does the crashing stop?

---

### Post by Jameshardy88 on 2009-01-05
i can try that however it will take me some time to establish if it works or not as the crashes only happen at the moment approx once a day as far as i can tell, i will get back to you if that appears to be the case. If it is would this mean that i can not use my wireless?

---

### Post by blazemore on 2009-01-05
I had a problem with wireless and kernel panics before. Try Googling the name of your wireless chipset and Ubuntu, to see if anyone else has had a problem.
It might not be the wireless, it might be overheating.

---

### Post by Jameshardy88 on 2009-01-05
just as an update upon freezing caps/num lock both stop working

---

