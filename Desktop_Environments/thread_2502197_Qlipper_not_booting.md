---
title: "Qlipper not booting"
date: 2024-11-05
forum: Desktop Environments
---

### Post by MarcoPau on 2024-11-05
Hi all, I am getting this:

```
terminate called after throwing an instance of 'std::bad_alloc'
```

while trying to boot Qlipper after recent upgrade to oracular

Can't seem to find a solution on Google.

Does anybody have a hint?

Thanks!

---

### Post by ActionParsnip on 2024-11-05
Qlipper is an application you run in Ubuntu (and similar). You don't "boot" applications, you launch them.

What is the output of:
```

lsb_release -a; uname -a; apt-cache policy qlipper

```

---

### Post by grahammechanical on 2024-11-05
I have had very little education in this matter. A short (5 - 10 minutes) internet search on bad-alloc gives me the idea that this message is saying that there is not enough memory for Qlipper. It may not be referring to system memory (RAM) but to the amount of memory allocated to the program.

Why are you loading Qlipper from the command line? It is my understanding that it is loads automatically. 

> By default Qlipper should autostart and should be on the bottom right of  your panel. If you need to get it running and it is not go to the menu Accessories &#8227; Qlipper. To launch it from the command line run

[https://manual.lubuntu.me/stable/2/2.4/2.4.5/Qlipper.html](https://manual.lubuntu.me/stable/2/2.4/2.4.5/Qlipper.html)

As a wild guess you could try un-installing Qlipper and then re-installing. Qlipper is a clipboard manager. It saves the user's copy actions. It may be you need to clear the clipboard history.

Regards

---

### Post by MarcoPau on 2024-11-05
I am trying to boot from command line since it is not booting automatically any more and was trying to troubleshoot.

---

### Post by MarcoPau on 2024-11-07
> **grahammechanical said:**
> As a wild guess you could try un-installing Qlipper and then re-installing. Qlipper is a clipboard manager.

Tried reinstalling with --purge but the same error shows up on command line start.

Any other path to follow? Maybe using another clipboard manager? Any recommended one?

Thanks again for helping!

---

### Post by ActionParsnip on 2024-11-07
Still waiting for the output of my commands.............

---

### Post by yancek on 2024-11-07
If you want help you need to explain a few things starting with posting the output of the commands suggested in post 2.  Also, the exact command you used in your terminal to try to start the application.  What did you update from and what did you update to?  An Ubuntu OS, the qlipper application?  What is oracular as an online search produces nothing related to computers?

---

### Post by MarcoPau on 2024-11-11
Sorry guys, I think I missed the line with the commands by reading with my smartphone.

Here's the output:

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.10
Release:        24.10
Codename:       oracular
Linux pau 6.11.0-9-generic #9-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct 14 13:19:59 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
qlipper:
  Installato: 1:5.1.2-1ubuntu5
  Candidato:  1:5.1.2-1ubuntu5
  Tabella versione:
 *** 1:5.1.2-1ubuntu5 500
        500 http://it.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```

@yancek oracular is the Ubuntu version I upgraded to.

Thanks again for helping!

---

### Post by ActionParsnip on 2024-11-11
Do you see the error in the original post when you run
```

qlipper

```
in a terminal? Does that create the message?

---

### Post by MarcoPau on 2024-11-12
> **ActionParsnip said:**
> Do you see the error in the original post when you run
```

qlipper

```
in a terminal? Does that create the message?

Exacly. That message is prompted when I try running qlipper in a terminal.

---

### Post by MarcoPau on 2024-11-13
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.10
Release:        24.10
Codename:       oracular
Linux pau 6.11.0-9-generic #9-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct 14 13:19:59 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
qlipper:
  Installato: 1:5.1.2-1ubuntu5
  Candidato:  1:5.1.2-1ubuntu5
  Tabella versione:
 *** 1:5.1.2-1ubuntu5 500
        500 http://it.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Please note I have lsb-release and lsb-core packages installed.

---

### Post by davetheoldcoder on 2024-11-15
> **MarcoPau said:**
> Any other path to follow? Maybe using another clipboard manager? Any recommended one?

On Ubuntu 24.04.1, I'm using the Gnome extension GPaste (package: gnome-shell-extension-gpaste). It has some settings that I don't understand, but it works adequately.

---

### Post by MarcoPau on 2024-11-17
Thanks for the hint Dave, unluckily that package is bringing in ove 250 MBytes of dependencies.

Let's see if I can manage fixing Qlipper or find a lighter installation.

---

