---
title: "wireless utility not showing up"
date: 2012-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jzp706 on 2012-09-28
my wireless driver is downloaded and installed(i think) but on the wireless icon it does not have anything for wireless connections on it. help asap:confused::(
 
 
i can clarify. there is no mention of the word wireless in the connections dropdown. i am using a dell inspiron e1501 and 12.04. please help.

---

### Post by kc1di on 2012-09-28
> **jzp706 said:**
> my wireless driver is downloaded and installed(i think) but on the wireless icon it does not have anything for wireless connections on it. help asap:confused::(
 
 
i can clarify. there is no mention of the word wireless in the connections dropdown. i am using a dell inspiron e1501 and 12.04. please help.

Hi jzp706 and welcome to Ubuntu,

A little more information would be helpful. When you say the drivers are downloaded and installed just how did you install them?

Did you use the Additional Driver Tool? (aka- jockey)

if not what drivers did you install. 
Can you tell us what wireless card your machine uses?

If not could your run this command in a terminal and post the 
results here.

Command: ```
lspci
```
That a lower case L not #1.

if it is a wlan mini card it's most likely a broadcom 4312 or similar and requires the Broadcom-sta driver.

---

### Post by jzp706 on 2012-09-28
i did run the additional drivers utility. it is a broadcom sta 4311

---

### Post by jzp706 on 2012-09-28
i have been trying to find the problem for about 2 hours now.

---

### Post by kc1di on 2012-09-28
> **jzp706 said:**
> i did run the additional drivers utility. it is a broadcom sta 4311

this may sound simple but did your reboot after installing the driver?

---

### Post by jzp706 on 2012-09-28
yes i did. where it should say wireless connections it just says "disconnected"

---

### Post by jzp706 on 2012-09-28
i really need this fixed. i have a project that i need to work on for school and needs to be done b4 monday. i need this to work. it is of the highest priority.

---

### Post by kc1di on 2012-09-28
It seems there may be a bug in the 4311 and the wired driver.
see this page for details. 
May be the same procedure would get you up and running.

[http://askubuntu.com/questions/139168/dell-1390-wireless-bcm4311-ubuntu-12-04-no-wireless-icon-in-unity]("http://askubuntu.com/questions/139168/dell-1390-wireless-bcm4311-ubuntu-12-04-no-wireless-icon-in-unity")

This page may also be helpful:
[http://codeghar.wordpress.com/2012/07/12/get-broadcom-bcm4311-working-in-ubuntu-12-04/]("http://codeghar.wordpress.com/2012/07/12/get-broadcom-bcm4311-working-in-ubuntu-12-04/")

---

