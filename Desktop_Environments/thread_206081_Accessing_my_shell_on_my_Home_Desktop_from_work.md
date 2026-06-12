---
title: "Accessing my shell on my Home Desktop from work"
date: 2006-06-29
forum: Desktop Environments
---

### Post by jimycad on 2006-06-29
Hi All,

I've recently installed Ubuntu Desktop (6.06) on my home PC. I wish to do some administartion on that machine via my Unix workstation at work... I did enable ssh on my home PC but I found that I was not able to use ssh from my unix machine. Any suggestions? I'm open to telnet or rlogin and I am aware of the security risks involved... bottom line, I'd like to get shell access remotley to my linux box at home.

Also I may be limited to my current unix enviroment as software for HP-UX is quite limited. Telnet and rlogin both work on the workstation.

Thanks,
jimycad

---

### Post by Dubbayoo on 2006-06-29
If you have the ability to install ssh on your work computer do so. It is a clearly superior and more secure alternative to the others. You might even look into ssh host keys while you're at it.

---

### Post by shrift on 2006-06-29
This really doesn't sound like an ubuntu problem at all. Maybe the forums for the OS your running at work would have some insight? 

I am reasonably certain that ssh can run on just about every unix environment known to man. There may be other issues, with versions etc... But, maybe they can help you with all that.

OR, are you telling us that you have SSH on your unix PC, but you are for some reason not able/allowed to use it?

---

### Post by jimycad on 2006-06-30
I'll see if I can get ssh installed on my Unix box...  Any special instructions on setting up the ssh on my desktop?

---

### Post by ohgod on 2006-06-30
run this to get the ssh server installed:  sudo apt-get openssh-server

---

### Post by shrift on 2006-06-30
[QUOTE=ohgod]run this to get the ssh server installed:  sudo apt-get openssh-server[/QUOTE]
That is almost it:
```
sudo apt-get install openssh-server
```

Or you can use synaptic. It's in the System>Administration>Synaptic Package Manager

---

