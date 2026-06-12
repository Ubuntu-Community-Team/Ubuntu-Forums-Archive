---
title: "Synaptic Package Manager won't launch"
date: 2006-06-29
forum: Desktop Environments
---

### Post by mmcdonnell on 2006-06-29
Hello.  I just installed 6.06 LTS on a Dell XPS T500 pc today.  This is my first time to install Ubuntu and it looks and feels class so far, but, the Synaptic Package Manager won't launch.  I also cannot add any new applications and also when I go to install any of the 76 updates they won't install either :confused: 

Is there anything that I can do to resolve this??

The pc is on a broadband connection and everything else seems to be working fine.

Any help much appreciated =D> 

Thanks,

Marcus

---

### Post by Rui Pais on 2006-06-29
Hi,
what are the error messages when you launch synaptic or update-manager from a terminal?

Whats the output of 
```
sudo apt-get upgrade
```

---

### Post by everett3rd on 2006-07-03
I am having this same problem I think.

Synaptic, Add/Remove and Upgrade Manager all start, but them they shut down with no error or anything.

This is the error I get when running the code above.

sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%

Thanks in advance.

Everett

---

### Post by Rui Pais on 2006-07-03
Hi,
maybe you have a corrupted apt cache. Try:
```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```
to see if thats go back to normality.

good luck

---

### Post by everett3rd on 2006-07-03
That did it!

I humbly thank you and sacrifice 2 Windows XP Installs in your honor.


Everett.

---

### Post by Rui Pais on 2006-07-03
[QUOTE=everett3rd]That did it!

I humbly thank you and sacrifice 2 Windows XP Installs in your honor.


Everett.[/QUOTE]

hey everett3rd, i'm deeply touched. 
Nobody never, ever, sacrifice a thing for me, not a goat or even a small pigeon... 2 full WindowsXPs! Thats a honour.

Lets blood those creatures right away :evil: 

:lol:
glad i could help 

have fun ;)

---

