---
title: "Display Problem"
date: 2007-12-11
forum: Desktop Environments
---

### Post by dieg0 on 2007-12-11
So, I installed ubuntu 7.10 and it was going fine until i went to put in my monitor and resolution. I must have put in the wrong one or something and now i can see anything to change it back. All i can see on the screen is my desktop about 5 times across and I am unable to go back and change it. Is there anyway i could fix this even though the screen wont show the desktop correctly?

Thanks

---

### Post by Lostincyberspace on 2007-12-11
Do you see the desktop?
If that is correct right click on the desktop and click create launcher, in the input are type in xterm or whatever terminal.
then click on it and run
```
xrandr -s n
```
Where "n" is the resolution you want.

---

### Post by dieg0 on 2007-12-11
yes i do, but its really blurry so it's no good to me. Its also tiled across the screen so when i move the mouse it's moving on 5 different places at the same time.

---

### Post by Lostincyberspace on 2007-12-11
I just finished editing my post with more instruction so you should be able to follow them.

---

### Post by dieg0 on 2007-12-11
I'm unable to do that. On my screen i just looks like an orange mess and i can't make it out enough to do what you said.

---

### Post by Lostincyberspace on 2007-12-11
Can you use ctrl+alt+f2 to get to a terminal if you are you can still use the command there.

---

### Post by dieg0 on 2007-12-11
rawr. didn't work. I got to the terminal and it looked fine. I put in
```
xrandr -s 1680x1050
```
is that right?

---

### Post by Lostincyberspace on 2007-12-11
I am not sure I found it online there is a manual I found that might help though.
[http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

---

