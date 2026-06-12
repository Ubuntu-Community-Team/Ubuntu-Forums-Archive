---
title: "Upgrading to i686 and RAM question"
date: 2005-07-29
forum: Desktop Environments
---

### Post by c0rderr0y on 2005-07-29
1st post....
 here goes... just wondering if upgrading to the 686 kernel breaks anything?


also all my ram isnt being shown in Kinfo i have 1 gig but it shows only 885.41MB hopefully someone can help me out here

---

### Post by hod139 on 2005-07-29
I haven't had any problems with the 686 kernel, and would recommend upgrading to it.  As for the memory, what does the first line of 
/proc/meminfo
say?

---

### Post by c0rderr0y on 2005-07-29
1st line says

MemTotal:   906660 kB

---

### Post by az on 2005-07-29
Install the 686 smp kernel.  SMP will recognise all your ram.


No, there is no danger of breaking anything.  If you cannot boot your new kernel, you still have the option of booting the old one.  Once you are happy with the new kernel, you can remove the old one by removing the linux-image-2.6.10-5-386 package.

---

### Post by c0rderr0y on 2005-07-29
is there a difference between 686 and 686 smp ? or are they one and the same?

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]is there a difference between 686 and 686 smp ? or are they one and the same?[/QUOTE]
SMP (symmetric multi-processing) is needed if you have multiple processors.

---

### Post by Xian on 2005-07-29
Of course all this is assuming you _should_ be running a 686 kernel. :)

Run the command below in a terminal.
Make sure that you have an output similar to mine.

Look for the trailing 'i686 GNU/Linux'.
That is what your system is capable of running.

```
$ uname -a
Linux linux 2.6.10-5-k7 #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux
$
```

---

### Post by c0rderr0y on 2005-07-29
what other packages do i need to install with the linux-image ? do i need the headers?

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]what other packages do i need to install with the linux-image ? do i need the headers?[/QUOTE]
You don't need the headers to boot into the kernel.
They are required for some applications to build upon.

Installing them will do no harm but they are not required.

---

### Post by c0rderr0y on 2005-07-29
awsome you guys are a big help i have installed kubuntu on a friends laptop and now another friend wants it... so im going to have to be their kubuntu guru..... but .... yes there is a but im not used to a debian based linux... i came from slackware kuz my lappy is too new for slack.

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]awsome you guys are a big help i have installed kubuntu on a friends laptop and now another friend wants it... so im going to have to be their kubuntu guru..... but .... yes there is a but im not used to a debian based linux... i came from slackware kuz my lappy is too new for slack.[/QUOTE]
Slackware is a great distro. But if you can learn that type of system, Debian will certainly be no more difficult. Ubuntu makes it easy with all of the nice starter guides, how-to's, configuration tools, and the developing wiki. Not to mention the Apt package management system.

Plus you have us. :)

---

### Post by c0rderr0y on 2005-07-29
yes i hated having to look for dependencies in slack  :???:  but i love how its  stable, customizable, and FAST, now i love kubuntu AND slackware

---

