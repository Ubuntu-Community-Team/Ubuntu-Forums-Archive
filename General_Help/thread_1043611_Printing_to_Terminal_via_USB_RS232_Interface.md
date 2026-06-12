---
title: "Printing to Terminal via USB RS232 Interface"
date: 2009-01-18
forum: General Help
---

### Post by dbsoundman on 2009-01-18
This probably sounds kind of convoluted, here's the story...

I'm trying to get the "print" output from one device to appear on a terminal window in linux. Basically it would be as if I was using my computer as a printer connected to this device. The device has RS232 out, so I bought an RS232 to USB adapter as neither of my computers have serial connectors on them. My question is, what do I have to do to set up the terminal to "grab" this output? I tried searching around but all I could find was info on how to setup printers.

Thanks!

-Dan

---

### Post by mssever on 2009-01-19
Basically, you need to redirect the output to the proper device. You can find the device by looking at the output of the w command. For example, in terminal window A I typed this: ```
~:$ w
 23:57:39 up 8 days, 14:47,  3 users,  load average: 0.53, 0.64, 0.85
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
scott    tty9     :0               Fri15    8days  3:20   0.48s x-session-manager
scott    pts/0    :0.0             Fri15    4:40m  8.74s  4.18s bash
scott    pts/1    :0.0             13:33    0.00s  4.30s  0.02s w
```The line with the w command at the end is the current terminal. The TTY column gives the device name.

From terminal window B, I typed the following, based on the info above:```
~:$ echo "Hi" > /dev/pts/1
```and the word "Hi" appeared on terminal window A.

---

