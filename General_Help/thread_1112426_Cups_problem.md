---
title: "Cups problem"
date: 2009-03-31
forum: General Help
---

### Post by illbashu on 2009-03-31
Hi, i installed cups but i cant figure out how to start it, i tried running the code to restart it but its saying it doesn't exist :/

```
bash@bash-desktop:~/Desktop/cups-1.3.9$ sudo /etc/init.d/cupsys restart
sudo: /etc/init.d/cupsys: command not found

```

I tried opening "/etc/init.d/cupsys" but its an doesn't exist, its was an empty file when i gedited it.

---

### Post by duckegg123 on 2009-04-02
I have exactly the same problem. This was my attempt.

Prompt:~$ sudo /etc/init.d/cupsys restart
sudo: /etc/init.d/cupsys: command not found

The answer may be that "cupsys" has been replaced by "cups". It seemed to be on the right track,  However, it gave me a failed outcome:

Prompt~$ sudo /etc/init.d/cups restart
Restarting Common Unix Printing System: cupsd                                
cupsd: Child exited with status 1! [fail]
Prompt:~$

So I used the "troubleshoot" option under >System>Administration>Printers and this told me:

The CUPS spooler does not appear to be running.
To correct this look for the CUPS service in
System>Administration>Services 

I duly did this but there was no CUPS service there to select. I spent the day researching this but could not the CUPS service running.

---

