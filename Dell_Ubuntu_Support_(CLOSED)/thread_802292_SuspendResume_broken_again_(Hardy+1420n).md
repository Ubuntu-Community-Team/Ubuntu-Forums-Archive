---
title: "Suspend/Resume broken again (Hardy+1420n)"
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2008-05-21
For a while there, suspend/resume was working fairly well.  About 1/5 times it would not resume.  Now it is more like 2/3 times it does not resume.  This is getting frustrating as depending on a functional laptop is important for my work.

Does anyone know of a way to debug/investigate these resume failures?  It seems we need a guide to dealing with this issue.

---

### Post by sam_delta on 2008-05-21
i dont know much but just curious, how big is your swap partition?

sam

---

### Post by aidave on 2008-05-21
8.42 GB,
my laptop has 4GB RAM

What would be the ideal size?

---

### Post by sam_delta on 2008-05-21
you definetly have enough SWAP, as i told you before, i dont know much, but if you tell me which video card you have, ill do my best to research on your problem, ive heard that video drivers might be a factor for this,


sam

---

### Post by aidave on 2008-05-22
It comes with an NVIDIA card...

Do you know of any logs that are created when suspending and resuming?

---

### Post by sam_delta on 2008-05-22
check out system>administration>system log, ,, and find the date/time when you suspended/resumed

sam

---

### Post by sam_delta on 2008-05-22
also, after doing some research, are you using propetary drivers?
here are some fixes i found, havnt tryed them but might be usefull to you

i believe that suspend/hibernate works fine with the open source "nv" drivers, but here are some fixes for propetary drivers

Note: those links are some of the answers that i got from googling "ubuntu suspend with nvidia", i duno if they will work, you should research a bit more for fixes for your specific drivers

personally i would research on a specific fix for the driver you are using.

Suspend nvidia/ati fix
[http://ubuntuforums.org/showthread.php?t=327868](http://ubuntuforums.org/showthread.php?t=327868)

HOWTO get Hibernate working with Proprietory Nvidia driver (using Suspend2)
[http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)


sam

---

### Post by aidave on 2008-05-22
Thanks, I will try all your advice and post back the results!

---

