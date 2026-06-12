---
title: "In Python van not draw graph, error is cannot connect to DISPLAY"
date: 2017-10-11
forum: Desktop Environments
---

### Post by deepakdeshp on 2017-10-11
Hello,
1.I am trying to plot a graph but am getting error. Can somebody suggest please?
2. Is there any way to check the hardware including cpu? I am running Mint 18.2 with Intel processor.

```
echo $DISPLAY
:0xhost +
No protocol specified
xhost:  unable to open display ":0"


girish@girish:~$ import matplotlib.pyplot as plt
No protocol specified
import: unable to open X server `:0' @ error/import.c/ImportImageCommand/364.
girish@girish:~$ python
Python 3.6.1 |Anaconda 4.4.0 (64-bit)| (default, May 11 2017, 13:09:58) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import matplotlib.pyplot as plt
>>> plt.plot([1,2,3,4])
No protocol specified
QXcbConnection: Could not connect to display :0
Aborted (core dumped)

```

---

### Post by deepakdeshp on 2017-10-12
The problem is solved as I was doing > su - user1 this would not allow opening of xterm of the original user.

---

