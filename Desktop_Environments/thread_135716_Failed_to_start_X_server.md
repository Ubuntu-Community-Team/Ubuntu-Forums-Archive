---
title: "Failed to start X server"
date: 2006-02-24
forum: Desktop Environments
---

### Post by peppermint on 2006-02-24
Hi,
	Ive just installed ubuntu 5.10 onto my desktop PC. The installation process went well, but now every time i start up the system i get an error. It says...

```

Failed to start X server (your graphical interface).
It is likely that it is not set up correctly. Would you like
to view the X server output to diagnose the problem?
<Yes>   <No>

```

Upon clicking yes, another blue screen is displayed with lots of details on it. Far too many for me to copy over here. At the bottom of the details it points to a log file with the details in it, if i can figure out how to get the contents of the log file into this thread through the command line, I will post them here. In the mean time, could you suggest as to what has gone wrong and what the sollution could possibly be?

---

### Post by LordBug on 2006-02-24
More than likely you have the wrong X server specified, or it's mis-configured.

Need to know what kind of video card you have, and what the contents of your /etc/X11/xorg.conf file are (specifically the video sections).

---

### Post by heimo on 2006-02-24
Just try reconfiguring, and choose vesa driver (is less likely to fail).
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by peppermint on 2006-02-24
thanks heimo, works perfectly now :D

---

### Post by banjoallen on 2006-03-04
Hey. I'm new at this Linux stuff. I have the same problem and message. I'm trying to run the live CD on a WinXP computer.when I get to this message I can't go any farther. I think I understand that these code's are a command prompt. At the bottom of the error message there is an area that will take stuff from the keyboard. Is this where I enter the suda code? thanks. Allen

---

