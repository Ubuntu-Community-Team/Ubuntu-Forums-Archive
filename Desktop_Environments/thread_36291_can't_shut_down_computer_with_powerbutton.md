---
title: "can't shut down computer with powerbutton"
date: 2005-05-22
forum: Desktop Environments
---

### Post by dragonheart73951 on 2005-05-22
Hello! I've got a strange issue: I can't shut down the computer with the powerbutton anymore! (it used to work!) 

I found the following messages in /var/log/acpid: 
  
 [Wed May 11 14:42:57 2005] received event "button/power PWRF 00000080 00000003" 
 [Wed May 11 14:42:57 2005] executing action "/etc/acpi/powerbtn.sh" 
 [Wed May 11 14:42:57 2005] BEGIN HANDLER MESSAGES 
 DCOPClient::attachInternal. Attach failed Could not open network socket 
 DCOPClient::attachInternal. Attach failed Could not open network socket 
 ERROR: Couldn't attach to DCOP server! 
 DCOPClient::attachInternal. Attach failed Could not open network socket 
 DCOPClient::attachInternal. Attach failed Could not open network socket 
 ERROR: Couldn't attach to DCOP server! 
 [Wed May 11 14:43:21 2005] END HANDLER MESSAGES 
 [Wed May 11 14:43:21 2005] action exited with status 1 
 [Wed May 11 14:43:21 2005] completed event "button/power PWRF 00000080 00000003" 
 
I think, the push on the button is acknowledged and the skript is carried out - but I can't understand whats going on afterwards!
Des anyone understand the messages here? (what is this about dcop? is it a KDE-specificproblem?)

---

### Post by dave9191 on 2005-05-22
Yeh, it looks like a KDE spesific thing. DCOP is a way to give KDE apps a command line interface. The powerbtn.sh file is trying to shut down all the kde apps but something is not working. How to fix it, I dont know, but there is a brute force solution. 

Edit the /etc/acpi/powerbtn.sh file and comment out every line (put a # at the start of it) apart from 

/sbin/shutdown -h now "Power button pressed"

This might result in open kde apps loosing data and not asking you if you want to save, so make sure you save everything first.

---

### Post by dragonheart73951 on 2005-05-24
this solution works fine for me - thank you!
:-)

---

### Post by dave9191 on 2005-05-25
No probs :)

---

