---
title: "Running a command at startup or resume from suspend/hibernate"
date: 2006-09-01
forum: Desktop Environments
---

### Post by aka5ha on 2006-09-01
Hi Everyone,

A n00b question but thanks in advance for your help.

I run my Wi-Fi card at low power to save power using:
iwconfig -eth0 txpower=1mW

Which I have to type every time I boot or resume from hibernate/suspend.  

Is there a place I can put this so that it is run at every boot, and also every time I resume?  

Thanks very much!

---

### Post by Nytram on 2006-09-01
Hi,

This is how I run startup programs:

System/Preferences/Sessions
Choose the StartupPrograms tab, and Add a command

This runs software when booting up, I don't know about resume because I've not used it.

HTH

---

### Post by aka5ha on 2006-09-01
Thank you, that is a big help!  

Since resuming from suspend/hibernate takes about as long as a fresh boot, if nobody knows how to solve for suspend/hibernate, I will not use that any more, just shut down.  

Regards,

Aka5ha

---

### Post by aka5ha on 2006-09-01
Hi,

It turns out that putting sudo iwconfig eth1 txpower 1mW in the system->prefs->sessions->startup programs does not work.

It does not execute the command upon startup.  When I check the Wi-Fi card state using iwlist eth1 txpower it reports 100mW.  

Any other suggestions appreciated!

---

