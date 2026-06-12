---
title: "I did somethin bad..."
date: 2006-01-13
forum: Desktop Environments
---

### Post by Vevmesteren on 2006-01-13
I think, well I installed Ubuntu two days ago and am in heaven. well almost anyway, I really like what I have seen until now. Today I was going ahead with installing Eclipse, which I really need. Well one thing lead to another and I managed to set my accounts home directory to a non existing location. Ubuntu obviousely ends up being confused, and tells me I cannot boot anyomre. I have managed to bring up the terminal window, how can I now reset my home dir to an existing location? /home/vevmesteren/ is invalid I am told, though I am fairly certain it exists...I have logged onto the terminal and there I can see get into home (cd home) and I can see my /vevmesteren/ directory...

any pointers would be greatly appreciated. the current home dir is set to /home/vevmesteren/ why does this not work and how can I fix it? I have been trying to find things in this forum and elsewhere without much luck. 

please help....

---

### Post by Zimmer on 2006-01-13
A 'LIVE' CD may help here,. Have you got the Ubuntu Live CD? Or any other? Knoppix, SimlyMepis? 
If you boot a live CD you may be able to 'find' where the directory has gone to and copy it back to the correct location....(note the use of the word 'may' ).
Difficult to diagnose at this distance what has happened...
Regards

---

### Post by adwait on 2006-01-13
use 
```
sudo usermod -d <new home direcotry>
```

---

### Post by rjwood on 2006-01-13
If you are at the command line you are proably in your home directory. type 'ls' and see what comes up.

---

