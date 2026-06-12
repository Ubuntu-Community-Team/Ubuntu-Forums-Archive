---
title: "Remote terminal to Ubuntu from Win XP"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Aggienator on 2006-08-31
Can someone help? At work I have windows XP on my PC, but have recently added an Ubuntu machine to the network. At the moment this is taking up room in my office! What I would like to do is tuck this machine out of the way, but still be able to get a terminal session on it remotely from my XP PC. 

I suspect I need to use SSH, is this right?

If so how do I go about setting it up and what do I need on the XP PC to use it?

Thanks for any advice!

---

### Post by Ramses de Norre on 2006-08-31
On ubuntu: ```
sudo aptitude install ssh
```

On windows: download putty.exe [here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") and run it, give in your ip and things like that and you'll be able to ssh into your ubuntu box which will give you a shell.

If there is a router in between the two machines you might need to forward port 22.

---

### Post by Aggienator on 2006-08-31
Having installed SSH do I need to run something? There is just a switch between the two machines, but when I try putty I get a connection time out error?

Thanks

---

### Post by Aggienator on 2006-08-31
Hmm, Ive made a bit of progress, restarted my Ubuntu machine, now I get "access denied". Do I have to put a password in putty somewhere? (i'm putting [email]username@xxx.xxx.xxx.xxx[/email] as my hostname in putty)

---

### Post by Aggienator on 2006-08-31
Cracked it, it was openssh-server I needed to install (done via Synaptic).

Thanks Ramses for getting me on the right track :-)

---

### Post by ayoli on 2006-08-31
If you have installed putty click on your Start button, click on Run, and type in "c:\path\to\putty" (here, i suggest you to install it in c:\windows\command or any path which is PATH environement variable to avoid type in path each time). This brings up the PuTTY Configuration window, where you can set a session fill username and hostname fields, save the session and run it, you will be prompted for your password.
regards.

---

### Post by ayoli on 2006-08-31
> **Aggienator said:**
> Cracked it, it was openssh-server I needed to install (done via Synaptic).

Thanks Ramses for getting me on the right track :-)

arf ! yes openssh-server required to do that :)
have fun with remote CLI.

---

### Post by Aggienator on 2006-09-01
Thanks Ayoli, can now try to get to grips with PHP/MySQL and setting up MySQL without having my desk covered in kit!

---

