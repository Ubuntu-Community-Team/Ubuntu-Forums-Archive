---
title: "Held Packages Under Kynaptic"
date: 2005-08-01
forum: Desktop Environments
---

### Post by WiFi Net Guy on 2005-08-01
Hi, all. 

When I install something under Kynaptic, I always have some "held packages". What are they and how do I "unheld" them? 

Thanks in advance...

---

### Post by Xian on 2005-08-01
The easiest way to uncover this is to open a terminal and instruct apt to install one or some of the packages being held back. It will then provide some output which should specifically describe the block which is being encountered. If that output does not make sense to you then just paste it in your next post and we should be able to give you further assistance.

```
$ sudo apt-get install packagename
```

---

### Post by psychobuffalo on 2005-08-01
You might consider installing Synaptic - a much better program for handling packages/updates.

---

### Post by Xian on 2005-08-01
[QUOTE=psychobuffalo]You might consider installing Synaptic - a much better program for handling packages/updates.[/QUOTE]
Synaptic only places a GUI front end on Apt.
It may be more intuitive but it will not reduce the number of held pkgs.

---

### Post by AndyAWS on 2005-08-01
But if you use Synaptic you won't have to jump to the terminal and use apt-get to find out why a package ins't installing, Synaptic will give you basically the same feedback that apt-get does.

---

### Post by Xian on 2005-08-01
[QUOTE=AndyAWS]But if you use Synaptic you won't have to jump to the terminal and use apt-get to find out why a package ins't installing,[/QUOTE]
And if you use a terminal you won't have to jump to Synaptic. :)

But seriously, the member said they were using Kynaptic.
Is it crippled in the context of held pkgs compared to Synaptic?

---

### Post by psychobuffalo on 2005-08-02
[QUOTE=Xian]Synaptic only places a GUI front end on Apt.
It may be more intuitive but it will not reduce the number of held pkgs.[/QUOTE]
I was only mentioning Synaptic because it is nicer to use and gives more options than Kynaptic - I didn't mean to imply that it doesn't hold packages.

---

