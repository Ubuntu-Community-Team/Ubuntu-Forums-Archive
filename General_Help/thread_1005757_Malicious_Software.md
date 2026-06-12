---
title: "Malicious Software"
date: 2008-12-08
forum: General Help
---

### Post by ToyotaGuy23 on 2008-12-08
Here's a question,

If your Ubuntu machine runs funny, should you scan for virus/malware?

What apps should I look for to scan for virus', trojans, general malware?
The repos had something called 'virus scanner' but I dunno about it. 

If you suspect your ubuntu machine may be infected, what should you do?

PS 
I know ubuntu isn't affected by infections the same way as more popular operating systems.

---

### Post by bodhi.zazen on 2008-12-08
See the security section for security tips, starting with the sticky.

If your computer is acting odd, start with the usual tools such as 

top

free

and look in the logs for errors.

---

### Post by phidia on 2008-12-08
Maybe you want to clarify "runs funny" but you can find more info on this topic and also virus detection software [here]("https://help.ubuntu.com/community/Antivirus").

---

### Post by 2hot6ft2 on 2008-12-08
wine. You probably already have clamav installed so synaptic and install clamtk then it will be in Applications>System Tools>Virus Scanner

---

### Post by cmay on 2008-12-08
> **ToyotaGuy23 said:**
> Here's a question,

If your Ubuntu machine runs funny, should you scan for virus/malware?

What apps should I look for to scan for virus', trojans, general malware?
The repos had something called 'virus scanner' but I dunno about it. 

If you suspect your ubuntu machine may be infected, what should you do?

PS 
I know ubuntu isn't affected by infections the same way as more popular operating systems.
the first six month i used linux i did like i would do on wiindows and got one program which was a basic compiler i really wanted to have so i rusted it and installed it. then i noticed some terminal commands did not work. and i checked whit rkhunter which fond nothing. but when i checked the actual folders in the system half the files in the /usr/bin was missing. simply wiped of the system. and i only found out something was wrong becouse i got no program from running the isntaller script and it was also gone. erased all the folders i downloaded and my home folder files was gone.  

if something like that happens the no ohter thing to do than simply reinstall the whole system and create a stronger password maybe also a good idea. 
but to avoid it then just use apt-get or synaptic and be satisfied whit the almost 18000 programs in it. :)

---

### Post by ghantoos on 2008-12-08
You can try rkhunter or chkrootkit to check your system for potential rootkits:

```
sudo apt-get install rkhunter
sudo rkhunter -c
``````
sudo apt-get install chkrootkit
sudo chkrootkit 
```Hope this helps,
Cheers,

---

### Post by Camilia on 2008-12-29
> **cmay said:**
>  i noticed some terminal commands did not work. and i checked whit rkhunter which fond nothing. but when i checked the actual folders in the system half the files in the /usr/bin was missing. simply wiped of the system. and i only found out something was wrong becouse i got no program from running the isntaller script and it was also gone. erased all the folders i downloaded and my home folder files was gone. 
)

Does this mean someone hacked into your computer?

---

### Post by scorp123 on 2008-12-29
> **Camilia said:**
> Does this mean someone hacked into your computer? Or maybe he became a victim of a prank ... Sometimes people think that they are "funny" and they place malicious commands into scripts. You are tricked into believing that executing that command with "sudo" will install something ... but in fact you just gave absolute and unrestricted "root" powers to a harmful program which then can wreak havoc on the system ...

That's why people are told not to install things from shady web sites and why it's better to only trust software that comes from the repositories and is installed via the package manager.

---

