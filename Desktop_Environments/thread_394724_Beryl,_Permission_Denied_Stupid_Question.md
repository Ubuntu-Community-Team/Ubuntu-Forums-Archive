---
title: "Beryl, Permission Denied: Stupid Question"
date: 2007-03-27
forum: Desktop Environments
---

### Post by w1llywonka on 2007-03-27
Week 2 of trying to get Ubuntu & Beryl running.  When following the Beryl Nvidia installation instructions, I try and use:
sudo echo -e "\n## Beryl repository\ndeb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" >> /etc/apt/sources.list" 

I get: "bash: /etc/apt/sources.list Permission denied" 

I tried what is mentioned here"http://wiki.beryl-project.org/index.php?title=Ubuntu_Edgy_FAQ&printable=yes" but I couldn't get this explanation to work.  Granted, I am a noob and clueless.  Any help is appreciated.

---

### Post by sisco311 on 2007-03-27
in terminal:
```
 sudo sh -c "echo deb http://ubuntu.beryl-project.org/ edgy main|cat>>/etc/apt/sources.list"
```
```
cat /etc/apt/sources.list
```
the last line of this commands output must be: 
> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by w1llywonka on 2007-03-31
Many thanks.  Using Beryl now, very cool.

---

