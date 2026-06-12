---
title: "Launching firewall automatically in ubuntu"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Rick069 on 2006-02-22
Does anyone know how I can get firestarter to automatically launch whenever I boot into my desktop? It seems to already be that way in kubuntu, but not ubuntu. It gets kinda old having to launch it manually everytime.

---

### Post by heimo on 2006-02-22
You don't need to launch it to have firewall running. It's just a frontend. If you still would like to get it running automatically:
[http://www.ubuntuforums.org/showthread.php?t=26483](http://www.ubuntuforums.org/showthread.php?t=26483)

---

### Post by SuperBOB on 2006-02-22
I dont actually use it, so I dont know for sure...

But its most likely that firestarter is just the front end to the rules it creates with iptables... and those rules are in place whether firestarter is running or not

---

### Post by kaamos on 2006-02-22
Just check that (start at boot) box in firestarter preferences. You can check that its running with```
sudo /etc/init.d/firestarter status
```it should return> Firestarter is running...

---

### Post by byen on 2006-02-22
Here is what I did:

Step1:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden 
Order: 20
(Notes: this is to add firestarter to your start-up)

Step2:
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page 
username ALL=NOPASSWD:/usr/sbin/firestarter
(insert your login user name in place of the username)
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.

---

