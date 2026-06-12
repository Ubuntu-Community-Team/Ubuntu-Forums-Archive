---
title: "Add/Remove Application Error"
date: 2009-05-06
forum: General Help
---

### Post by ogi3neo on 2009-05-06
Hi, I'm new to Ubuntu and don't know much about computers.  When I try to go to my add/remove application, I get the following error: This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.  I assume that when it says "Check for broken packages with synaptic" it means use the Synaptic Package Moniter, but when I open that, I get this error: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help?

Thanks.

---

### Post by colau on 2009-05-06
> **ogi3neo said:**
> Hi, I'm new to Ubuntu and don't know much about computers.  When I try to go to my add/remove application, I get the following error: This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.  I assume that when it says "Check for broken packages with synaptic" it means use the Synaptic Package Moniter, but when I open that, I get this error: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help?

Thanks.
Which version of ubuntu you are using?

---

### Post by ogi3neo on 2009-05-06
9.04.

---

### Post by Virtualboxbuntu on 2009-05-06
Go to Applications>Accessories>Terminal. Type:```

sudo apt-get install -f
```
and press enter. Type your password (it will not appear) and press enter.

---

### Post by colau on 2009-05-06
> **ogi3neo said:**
> 9.04.
From terminal 
[html]
sudo cat /etc/apt/sources.list
sudo dpkg -l | grep synaptic
[/html]

---

### Post by ogi3neo on 2009-05-06
Okay, it came to a screen about installing Java.  It has a long user agreement and at the bottom it says <Ok>.  How do I confirm it? I tried pressing enter and clicking <Ok>.>  Go to Applications>Accessories>Terminal. Type: 	Code:
 	sudo apt-get install -f 
and press enter. Type your password (it will not appear) and press enter.

---

### Post by ogi3neo on 2009-05-06
Colau, I tried what you said and the Add/Remove still gets the same error.

---

### Post by colau on 2009-05-06
> **ogi3neo said:**
> Okay, it came to a screen about installing Java.  It has a long user agreement and at the bottom it says <Ok>.  How do I confirm it? I tried pressing enter and clicking <Ok>.
From terminal
```

sudo aptitude update
sudo aptitude install -f

```
Give the password every time it prompts.
What is the average download speed?

---

### Post by Virtualboxbuntu on 2009-05-06
> **ogi3neo said:**
> Okay, it came to a screen about installing Java.  It has a long user agreement and at the bottom it says <Ok>.  How do I confirm it? I tried pressing enter and clicking <Ok>.

Press Tab until <OK> is highlighted in red, then press enter. As this is in a terminal, you can't "click" on anything with your mouse.

---

### Post by ogi3neo on 2009-05-07
Okay, the Add/Remove Applications is working.  Thank you both so much. :)

---

### Post by Virtualboxbuntu on 2009-05-07
Always glad to help a fellow Linux user. You may want to mark your thread as 'Solved.'

---

