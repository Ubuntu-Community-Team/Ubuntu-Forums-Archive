---
title: "Instaliton"
date: 2006-01-17
forum: Desktop Environments
---

### Post by ge77inhigh on 2006-01-17
I am installing real player 10 gold on my computer. i downloaded on my desktop
this is what i did 
source@ubuntu:~$ chmod +x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

HOW TO INSTALL REALPLAYER10 from my desktop PLZ give me the COde my Root user name is source :confused: :confused: :confused: :confused: :confused: :confused: :confused :???: :???:

---

### Post by lamego on 2006-01-17
You dont seem to have the minimal knowlege for what you are trying to do.
First learn to install packages from synaptic and read some more documentation if you really need to install something from the shell later.

---

### Post by mustang on 2006-01-17
[QUOTE=ge77inhigh]I am installing real player 10 gold on my computer. i downloaded on my desktop
this is what i did 
source@ubuntu:~$ chmod +x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

HOW TO INSTALL REALPLAYER10 from my desktop PLZ give me the COde my Root user name is source :confused: :confused: :confused: :confused: :confused: :confused: :confused :???: :???:[/QUOTE]

Hi ge77inhigh,

see if this post helps:

[http://ubuntuforums.org/showpost.php?p=434074&postcount=3](http://ubuntuforums.org/showpost.php?p=434074&postcount=3)

---

### Post by christhemonkey on 2006-01-17
As lamego said, this is easier in synaptic, on the Administration menu.  Installing from prompt is something that can be slightly unnecesary when you have synaptic (although apt-get does have its benefits!)

---

### Post by ge77inhigh on 2006-01-17
i guess terminal is not for me. dont worry i know about spm and how to install application threw that but i dont know how to install application like aim when u have them downloaded at your desktop and what do to type in this termnial source@ubuntu:~$
just trying to learn so PLZ HELP

---

### Post by lamego on 2006-01-17
[QUOTE=ge77inhigh]i guess terminal is not for me. dont worry i know about spm and how to install application threw that but i dont know how to install application like aim when u have them downloaded at your desktop and what do to type in this termnial source@ubuntu:~$
just trying to learn so PLZ HELP[/QUOTE]

Ok, if you want to start using the shell here is a good place to start:
[http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=224](http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=224)

---

### Post by healychan on 2006-01-17
I guess the problem is that you downloaded the file in the Desktop directory, but you were doing chmod in your home.

So, lets try.```
cd ~/Desktop
ls
```if you see the RealPlayer10gold.bin

Do the chmod again. Then follow the instruction of Realplayer web site.
I asked something similar before, check this out[http://www.ubuntuforums.org/showthread.php?t=116397]("http://www.ubuntuforums.org/showthread.php?t=116397")

---

### Post by christhemonkey on 2006-01-18
[http://www.tuxfiles.org/]("http://www.tuxfiles.org/")
That site really helped me with learning linux.

---

