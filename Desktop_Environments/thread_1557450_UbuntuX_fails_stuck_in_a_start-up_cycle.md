---
title: "Ubuntu/X fails stuck in a start-up cycle"
date: 2010-08-20
forum: Desktop Environments
---

### Post by jenkinsp on 2010-08-20
I have 2 nvidia gfx cards and 4 screens. I recently installed ubuntu 10.04 and had trouble getting the 2nd card found by the system. I added vmalloc=256M to the grub startup and then it found the 2nd card. This worked fine. I then went into the nvidia-settings control panel, put 2 monitors on Twinview with the first card, and the same with the second. I then rebooted the computer.

Now, it starts up, the Ubuntu (10,04) loading screen loads, the dots move until they are all purple, then the computers fan slows down, X seems to start, then each of the 4 monitors flicker in turn and the fan speeds up for 1/4 of a second, then this cycles endlessly. I can see on the 4th monitor the flicker is accompanied by a message "CANNOT DISPLAY CHANGE INPUT TO 1620x1080 @ 50mhz" it something like that, its a bit too quick.

So my first question, is there anyway I can log into the system, grub logs straight into the system and does not give me any options as its the only OS installed. Is there a F5 safemode or command promt (like windows) I can press when Ubuntu loads so I can log in and reset it back to what it was or fine more information on whats wrong?

Secondly, any idea how to correct this problem?

thanks for any help =)

---

