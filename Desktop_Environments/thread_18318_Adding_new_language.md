---
title: "Adding new language"
date: 2005-03-05
forum: Desktop Environments
---

### Post by d8888 on 2005-03-05
Hi,everyone

I am a new user to Linux
I installed Ubuntu in Traditional Chinese
For some reasons,I want to switch to Simplified Chinese
However no matter what I do
(edit locale.gen ; locale-gen or dpkg-reconfigure locales selecting zh_CN .....)
gdm always dump a "Language XXXX does not exist,using system default" message to me.
What should I do?

thanks.

---

### Post by bored2k on 2005-03-05
> **d8888]Hi,everyone

I am a new user to Linux
I installed Ubuntu in Traditional Chinese
For some reasons,I want to switch to Simplified Chinese
However no matter what I do
(edit locale.gen  said:**
> 
 [QUOTE]sudo base-config 

???

---

### Post by d8888 on 2005-03-06
base-config didn't ask me about language ><

another weird thing happend......

after using dpkg-reconfigure locales to set zh_CN as default locale

gdm and gnome desktop still shows traditional Chinese
however the dpkg-reconfigure locales console dialog became simplified Chinese
weired......

---

### Post by d8888 on 2005-03-06
problem solved.....

The magic word is "shutdown and reboot"

still thanks a lot

---

### Post by bored2k on 2005-03-06
[QUOTE=d8888]problem solved.....

The magic word is "shutdown and reboot"

still thanks a lot[/QUOTE]
 could u manage to have multiple languages on? id really love having english/french/spanish on ..

---

### Post by d8888 on 2005-03-09
go to console window

./dpkg-reconfigure locales

and choose all the language you want

shutdown the machine
boot....

In GDM,choose language you want in "Language" button in lowerleft corner

if it says "Language blahblah not found,using system defaults"

shutdown the machine and reboot

finally,the problem will magically disappear

---

