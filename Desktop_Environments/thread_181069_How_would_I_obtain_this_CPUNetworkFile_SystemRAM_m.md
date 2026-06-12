---
title: "How would I obtain this CPU/Network/File System/RAM monitor?  (See image inside)"
date: 2006-05-23
forum: Desktop Environments
---

### Post by Getwild2 on 2006-05-23
Please forgive me if this is a repost but I am BRAND NEW to Ubuntu.  I've been a member here for a while but did a lot of reading before installing for the first time last night.  Anyway, to my question.  

I am cuious how I would obtain the cpu/network/file system/RAM monitor found here?  Please forgive me if this is your image but this monitor is exactly what I'm looking for.  How would I implement this?  

[IMG]http://www.lbcflint.org/cjs/images/monitor.jpg[/IMG]

Thanks SO MUCH in advance!  :-D

---

### Post by art on 2006-05-23
What you see is called conky. There are instructions in the howto section. But I would recommend to use gkrellm instead...

---

### Post by Getwild2 on 2006-05-23
[QUOTE=art]What you see is called conky. There are instructions in the howto section. But I would recommend to use gkrellm instead...[/QUOTE]
Okay, I'll check gkrellm out.  Do you know if there is a HOW-TO for getting gkrellm running?  I'm searching now and havent come up with anything yet.

THANKS!

---

### Post by art on 2006-05-23
From synaptic install gkrellm, or from terminal
```
sudo apt-get install gkrellm
```
Then one done with this from Applications->SystemTools launch gkrellm. Now move it wherever you want, change the settings to your liking. Also I would you use the invisible theme, which I attach. It will make gkrellm blend with the background. Once you downloaded it, 
```
unzip invizible.zip
mv invisible .gkrellm2/themes
```
Now right click on the gkrellm, and choose the theme.

---

### Post by Getwild2 on 2006-05-23
[QUOTE=art]From synaptic install gkrellm, or from terminal
```
sudo apt-get install gkrellm
```
Then one done with this from Applications->SystemTools launch gkrellm. Now move it wherever you want, change the settings to your liking. Also I would you use the invisible theme, which I attach. It will make gkrellm blend with the background. Once you downloaded it, 
```
unzip invizible.zip
mv invisible .gkrellm2/themes
```
Now right click on the gkrellm, and choose the theme.[/QUOTE]
Art, I'm sorry for my ignorance but when I sudo that command in my terminal I receive the following error:

cstiff@ubuntu:~$ sudo apt-get install gkrellm
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gkrellm
cstiff@ubuntu:~$

I'm probably too new at this to be attempting this so soon.  I've received this error no matter what piece of software I try to install.  I believe I'm missing something here.  

Thanks so much and again, I'm sorry to be a pest.

---

### Post by halfvolle melk on 2006-05-23
gkrellm is in the "universe" repository:
```
jz@bc:~$ sudo apt-cache policy gkrellm
Password:
gkrellm:
  Installed: (none)
  Candidate: 2.2.7-2ubuntu1
  Version table:
     2.2.7-2ubuntu1 0
        500 http://nl.archive.ubuntu.com breezy/universe Packages
```
You'll need to enable it. Here's how to do that:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Getwild2 on 2006-05-23
[QUOTE=halfvolle melk]gkrellm is in the "universe" repository:
```
jz@bc:~$ sudo apt-cache policy gkrellm
Password:
gkrellm:
  Installed: (none)
  Candidate: 2.2.7-2ubuntu1
  Version table:
     2.2.7-2ubuntu1 0
        500 http://nl.archive.ubuntu.com breezy/universe Packages
```
You'll need to enable it. Here's how to do that:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]
That worked!  Thanks so much!!  :mrgreen: 

Now I just have to figure out how to tweak this thing.  That's the fun part though.  :D

---

### Post by halfvolle melk on 2006-05-23
Ok, cool. Good luck and enjoy!

---

### Post by dmizer on 2006-05-24
[QUOTE=halfvolle melk]```
jz@bc:~$ sudo apt-cache policy gkrellm
```
[/QUOTE]
thank you for that little nugget, halfvolle melk.

---

