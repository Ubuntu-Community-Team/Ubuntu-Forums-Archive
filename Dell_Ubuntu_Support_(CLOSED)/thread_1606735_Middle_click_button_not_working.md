---
title: "Middle click button not working"
date: 2010-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by morad on 2010-10-26
Hi everyone,

I've got a DELL Precision M6400 and I have had 9.10 and 10.04 installed on it without any problems since I bought it. Now that I have upgraded to 10.10 the middle click button on the touch pad has stopped working. If I use the left+right click combination I can get the desired functionality but since my laptop has got the extra key it would be great if I could use that.

Any suggestions are most welcome.

---

### Post by tomaton on 2010-11-05
Hi,

I have similar problem on my HP Compaq 8510 since upgrade to Ubuntu 10.10. I tried "xev" to identify which button was clicked and found that left and middle button are identified as the same button 1. :-(
```
~# xev 
...
ButtonRelease event, serial 36, synthetic NO, window 0x5200001,
    root 0x27a, subw 0x5200002, time 12194768, (45,43), root:(1782,1033),
    state 0x110, button 1, same_screen YES
...
ButtonRelease event, serial 36, synthetic NO, window 0x5200001,
    root 0x27a, subw 0x5200002, time 12197227, (45,43), root:(1782,1033),
    state 0x110, button 1, same_screen YES
...
ButtonRelease event, serial 36, synthetic NO, window 0x5200001,
    root 0x27a, subw 0x5200002, time 12198354, (45,43), root:(1782,1033),
    state 0x410, button 3, same_screen YES

```I didn't change the mouse button mapping
```

~# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
~# xinput get-button-map 4
1 2 3 4 5 6 7 8 9 10 
~# xinput get-button-map 10
1 2 3 4 5 6 7 8 9 10 11 12 

```And I disabled the Emulate3Button in xorg.conf. Wrong driver or configuration? Can someone point to a right direction?

---

### Post by tomaton on 2010-11-19
It seems to be caused by the bug 612591 [https://lists.ubuntu.com/archives/kernel-bugs/2010-August/128711.html](https://lists.ubuntu.com/archives/kernel-bugs/2010-August/128711.html) which cause that middle button behaves as the left button. This affects only three button touchpads. My 3 button external USB mouse works as expected.

---

### Post by Gargoulf on 2010-12-16
Hi.
Same here on DELL M6500. Actually, the behaviour of the middle button is not exactly same as left. 
For example, if I have a finger on the touchpad before clicking middle button, it does absolutely nothing. 
In turn, clicking middle button without any finger on the touchpad results like a left-button. 

I am also waiting for a solution since in previous ubuntu versions I had no pb.

---

### Post by morad on 2011-01-24
I have the same here, my 3 button touchpad does not work but my external mouse is just fine and the middle button works without any problems

---

### Post by morad on 2011-01-28
This problem has been solved in the new kernel.
Today I installed 2.6.35-25 and found that the bug has been fixed

---

