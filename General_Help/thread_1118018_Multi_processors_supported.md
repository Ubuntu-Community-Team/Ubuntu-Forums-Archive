---
title: "Multi processors supported?"
date: 2009-04-06
forum: General Help
---

### Post by dmovad on 2009-04-06
Today I ran the command: grep "model name" /proc/cpuinfo

The output is as follows:

model name	:                   Intel(R) Xeon(TM) CPU 3.40GHz
model name	:                   Intel(R) Xeon(TM) CPU 3.40GHz
model name	:                   Intel(R) Xeon(TM) CPU 3.40GHz
model name	:                   Intel(R) Xeon(TM) CPU 3.40GHz

It looks to me as though the system is only seeing one of the two Quad Core Xeon processors that exist in this system, if my assumption is correct.  If this is true how do I tell the OS that there are 2 processors (8 cores)?  I am running ubuntu 8.04-server-64 on an Intel motherboard with 6 GB's of RAM.

Thanks...
Dave

---

### Post by 0cton on 2009-04-06
I dont think the system is having difficulties "seying" other processors
Idk why it shows only 4, but I really doubt it can't acces the other processor
and I think you should use other means to see the processors and not grep

---

### Post by itisbasi on 2009-04-06
system monitor should show all the processors...

---

### Post by dmovad on 2009-04-06
What other means will verify that ubuntu can see both processors and all cores?

---

### Post by KayakJim on 2009-04-06
> **itisbasi said:**
> system monitor should show all the processors...

What is the command for that?

My server has no GUI installed so everything I do has to be from the command line.

---

### Post by dmovad on 2009-04-06
I also have no GUI...

---

### Post by itisbasi on 2009-04-06
#sudo apt-get isntall xosview

and then run

#sudo xosview +cpu




PS: I don't think gnome system monitor has a command line interface

---

### Post by 0cton on 2009-04-06
[http://www.linuxquestions.org/questions/linux-hardware-18/how-to-find-number-of-cores-in-cpu-476930/](http://www.linuxquestions.org/questions/linux-hardware-18/how-to-find-number-of-cores-in-cpu-476930/)
also [http://www.redhat.com/magazine/022aug06/departments/tips_tricks/](http://www.redhat.com/magazine/022aug06/departments/tips_tricks/) (if you miss it out)
should show a more detailed output (and also number of processors)

---

### Post by KayakJim on 2009-04-06
The following command did the trick for me.
```
lshw -C CPU

```
Thanks for the help and information.

---

### Post by dmovad on 2009-04-06
I get the following output:

root@server:/# xosview +cpu
Can't open display named 

Any idea's?

---

### Post by KayakJim on 2009-04-06
The xosview command outputs to an X-Window, which a GUI-less server does not have.

---

### Post by fcuk112 on 2009-04-06
i have a dual-core cpu, by default hyper-threading was not enabled.  you should be able to see the number of CPUs that you have by entering 'top' in the command-line and pressing '1' to see the other CPUs.  if you don't get extra lines for the additional CPUs, try this:

drop to a command prompt and type
"sudo gedit /boot/grub/menu.lst"

Look for the line that says
"# kopt=root=/dev/hdb2 ro"
Leaving everything intact includign the pound symbol simply add
"ht=on"
You should now have this
"# kopt=root=/dev/hdb2 ro ht=on"

Save then file and run the command
" sudo update-grub"

When you restart the system you should see a noticable diffrence in performance.

on jaunty alpha-6, i did not have to do this - multi-threading was enabled by default.

hope this helps.

---

### Post by itisbasi on 2009-04-07
> **KayakJim said:**
> The xosview command outputs to an X-Window, which a GUI-less server does not have.

Yep....Am sorry...had forgotten that xosview was an x-based system monitor..

---

