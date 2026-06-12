---
title: "Programs started from terminal quit when terminal is closed"
date: 2007-11-15
forum: Desktop Environments
---

### Post by quickk on 2007-11-15
Hi everyone, 

    Why is it that when I start a program from the terminal (could be gterm or xterm), it closes when I close the terminal?  

For example, from the terminal window, I start gedit:

gedit &

Then I close the terminal window and gedit closes too, even though I specified that I wanted it to run in the background.  I've noticed that this happens in opensuse too.  It's a big problem because I need to remotely run some simulations, and I don't want the simulation to stop because my local machine crashed, or shut down, or I closed the terminal window.  

Any thoughts?

Thanks!

---

### Post by taurus on 2007-11-15
Because that app belongs to that terminal.  Even if you send it into background, it is still a child process of that terminal.  If you want to run something but want to shutdown the terminal, use the NOHUP command.

```
nohup gedit
```

---

### Post by quickk on 2007-11-15
Brilliant!  Thanks a million!

---

