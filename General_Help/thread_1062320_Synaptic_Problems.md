---
title: "Synaptic Problems"
date: 2009-02-06
forum: General Help
---

### Post by yusuo85 on 2009-02-06
I use 8.04-2, trying to install gnomebaker today I encountered a problem, it downloaded successfully through apt-get but stalls while actually installing, this has locked me out of synaptic and prevented me from installing any other programs, Its been installing now for 20 mins and refuses to let me do anything dpkg configure -a, doesnt do jack, any help

---

### Post by mb_webguy on 2009-02-06
Applications generally assume you know when you need to run them with superuser privileges and when you don't, and therefore don't include that in error messages telling you to run a certain command.

dpkg is one of those commands that almost always needs to be run with superuser privileges, so when it says to use the command "dpkg configure -a" to fix the problem, it really means you should run "*sudo* dpkg configure -a".

---

### Post by yusuo85 on 2009-02-06
mb_webguy appreciate the advice but that kinda obvious, anything that requires root access need a sudo in front, that is not my problem

---

### Post by TWO on 2009-02-06
> **yusuo85 said:**
> I use 8.04-2, trying to install gnomebaker today I encountered a problem, it downloaded successfully through apt-get but stalls while actually installing, this has locked me out of synaptic and prevented me from installing any other programs, Its been installing now for 20 mins and refuses to let me do anything dpkg configure -a, doesnt do jack, any help

This is probably a ruthless suggestion but why not just try and kill synaptic in the terminal with the *killall [name of application] *command? Then run the dpkg command in the terminal to try and fix the problem?

Edit: Consider accessing tty1 with ctrl + alt + F1 and run those commands there. You might want to make use of the *top *command to identify synaptic.

---

### Post by yusuo85 on 2009-02-06
just tried that is still telling me to run dpkg configure -a, thanks anyway two

---

### Post by mb_webguy on 2009-02-06
> **yusuo85 said:**
> mb_webguy appreciate the advice but that kinda obvious, anything that requires root access need a sudo in front, that is not my problem

That "kinda obvious" advice is the solution the overwhelming majority of posts about people trying to fix Synaptic by running "dpkg configure -a".  Without more details about your specific problem, I assumed your post was part of that overwhelming majority.  

For example, "doesn't do jack" isn't really that informative.  Are you getting an error message?  With a few more details about your problem, I might be able to provide a more useful answer.

---

### Post by yusuo85 on 2009-02-06
sorry for being a little cocky but that answer just sounded obvious to me, I do understand noobs out there could be stuck on that problem for hours.

Im not getting an error message what so ever it just says "setting up gnomebaker" and has hanged ever since

---

### Post by drs305 on 2009-02-06
I just tried installing gnomebaker and it took about 15 seconds after the download was finished. It did have to download "icedax" first, so you might try downloading and installing "icedax" first and see if it installs correctly.

---

### Post by zvacet on 2009-02-06
Can you go to the synaptic and try to reinstall Gnomebaker?Or you can also try

```
sudo apt-get -f install
```

---

