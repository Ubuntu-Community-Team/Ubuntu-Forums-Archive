---
title: "Crontab/ wallpaper changer problem"
date: 2005-04-04
forum: Desktop Environments
---

### Post by Jagera27 on 2005-04-04
I am trying to get the desktop background to change every so often. I have dowloaded  the MICHELL version of ranwp.sh and ran it manually from the console after chmod +x . But I can't get crontab to automate the process. The line I have inserted in /etc/crontab is

* * * * * /usr/bin/ranwp.sh

 (plus CR and newline). I thought this should make the screen change every minute?-just as a test. But nothing happens, even after a re-boot. Can anyone suggest anything?

tia 

Nick

---

### Post by Jagera27 on 2005-04-04
Silly misunderstanding. I hadn't run crontab itself to translate the script. Now its working fine. 

BTW I had to modify Michell's script slightly by adding 1 to the output of the random number generator. RANDOM produces integers from 0 to N and the program further down couldn't find files labelled 0 (and omitted the last file)

Nick

---

### Post by paretooptimum on 2005-06-14
I'm trying to get this script to run as well. Can you post yours? Mine only runs sporatially.

---

### Post by DrecoZA on 2005-07-01
Any luck with this ? also cant get it to work

---

