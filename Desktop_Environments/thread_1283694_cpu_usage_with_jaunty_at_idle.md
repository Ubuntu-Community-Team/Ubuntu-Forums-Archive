---
title: "cpu usage with jaunty at idle"
date: 2009-10-05
forum: Desktop Environments
---

### Post by snuffy47 on 2009-10-05
hello

I just install ubuntu on my old compaq presario 2100 AMD 2400M with ati graphics with up to 64mb shared memory and 1G of ram.

At idle after install it appears with system monitor that the cpu usage is around 30% at idle.is this normal?

---

### Post by tuxxy on 2009-10-05
Well for older CPU's it is possible yes.  I would have thought it would be around there or around 20% on a single core.  Dont forget about your background processes.

---

### Post by earthpigg on 2009-10-06
hi,

install htop, and run it at the terminal.

sort by CPU. see what is eating up CPU cycles.

take action from there.

---

### Post by Vaphell on 2009-10-06
Gui system monitor shows fake results, it adds a lot to the load, **top** run from terminal is much more reliable. I wouldn't be surprised if you get 5%

---

### Post by earthpigg on 2009-10-06
top or htop, it's your choice entirely... htop is a bit easier to use, top comes installed by default.

---

### Post by snuffy47 on 2009-10-08
how do I run htop

---

### Post by permant on 2009-10-09
> **snuffy47 said:**
> how do I run htop
type: "sudo apt-get install htop" in the terminal window
then :your password
after the installation, just type "htop" in the terminal window, htop wil list the usage of your cpu

---

### Post by snuffy47 on 2009-10-09
Thanks for the help

It appears that firefox is the most reasource using app

Sitting at idle htop shows around 5-8% cpu usage

---

### Post by earthpigg on 2009-10-09
got a lot of addons installed?

---

