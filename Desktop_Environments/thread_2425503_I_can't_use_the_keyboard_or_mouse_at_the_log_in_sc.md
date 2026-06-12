---
title: "I can't use the keyboard or mouse at the log in screen or boot loader"
date: 2019-08-26
forum: Desktop Environments
---

### Post by naomibrown on 2019-08-26
Hi,

I'm looking at my Dad's computer that has apparently been continually re-booting every few minutes once it gets to the log in screen for about a week or so (perhaps longer). I've now seen the same thing happen. It gets to a normal log in screen but it's not possible to input anything via the USB keyboard or USB mouse. I've plugged both into my laptop and they are working fine.

I can get to the GRUB boot loader and can use the keyboard here. If I choose recovery mode, I then don't have access to the keyboard any more and can't choose recovery mode. 

I can get to GRUB in command line mode, but then I get stuck as I don't know what to do to boot into safe mode or anything else. I've had a look and found a list of commands, but didn't understand what would be useful to use. 

Would it be best to use a liveCD to try to reinstall Ubuntu, or is there something better I should try first? 

Thanks! :confused:

---

### Post by Autodave on 2019-08-29
Can you give us some specs on the machine please?

Could be either hardware or software issue.  My first thought would be a power supply issue or memory issue.  Could be a myriad of other HW issues, too.  How many USB things are connected?  If more than keyboard and mouse, just try disconnecting all of them and see if it will boot.  If it does, then either too many are connected, one or more are drawing too much power, or the power supply is weak / failing.

---

### Post by cruzer001 on 2019-08-29
At the grub screen press

Ctrl + Alt + F1

That will take you to console, keyboard should work there.

---

