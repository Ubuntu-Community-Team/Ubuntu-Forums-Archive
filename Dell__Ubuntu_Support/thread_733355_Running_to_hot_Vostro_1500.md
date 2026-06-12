---
title: "Running to hot Vostro 1500"
date: 2008-03-23
forum: Dell  Ubuntu Support
---

### Post by Stealth1081 on 2008-03-23
Hi i have noticed that my vostro's cpu is running up to about 65 degrees under load then a restart.

I have seen threads for feisty but not for gutsy.

Can't install i8kutils from repositorys as is not in gutsy's atleast i can't find it. I don't know how to compile from source.

If anyone could help it would be apreciated.

Can supply hardware if needed.

---

### Post by adult swim on 2008-03-24
do you have all of your repositories checked in software sources?

---

### Post by Stealth1081 on 2008-03-26
Yes.

Thanks for the reply.

Including the back ports

---

### Post by adult swim on 2008-03-26
see if this works from your terminal
```
sudo apt-get install i8kutils gkrellm gkrellm-i8k
```

---

### Post by Stealth1081 on 2008-03-30
Thanks will try.

---

### Post by Stealth1081 on 2008-03-30
Here is the results of the code you asked me to try.

If you have any other ideas and are still want to help please let me know.

sudo apt-get install i8kutils gkrellm gkrellm-i8k
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package i8kutils

---

### Post by adult swim on 2008-03-30
try this
go system/administation/synaptic package manager
search for i8k
the first thing on the list should be gkrellm-i8k
click on the box and check mark for installation, once you do this it should automatically select all of the dependencies you will need for gkrellm and i8k
click apply
if all goes well, if it doesnt PM me and i will email you the i8kutils package, open a terminal and  run ```
sudo modprobe i8k force=1
```
then run ```
sudo gedit /etc/modules
```
when the text editor pops up at the end of the file go to a new line and type in 
```
i8k force=1
```
to get gkrellm running hit alt-F2 and type in grkellm
if you want this to run on startup go to system/preferences/sessions
when you get there click add, at the name type in fans or whatever you want, at command type in gkrellm
to configure gkrellm to run your fans, you will need to right click it towards where it displays your computer name and select configuraion.  go to plugins and make sure that i8k is selected.  once you do that you can select i8k from the menu on the left that drops down beneath plugins.  then you can set your fans to turn on at specifc temperatures

---

### Post by empty_tank on 2008-03-31
> **Stealth1081 said:**
> Hi i have noticed that my vostro's cpu is running up to about 65 degrees under load then a restart.
.

try installing dellfand.  It work on my vostro 1400n. Link:[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

---

