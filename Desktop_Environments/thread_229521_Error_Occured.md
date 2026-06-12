---
title: "Error Occured"
date: 2006-08-04
forum: Desktop Environments
---

### Post by KDayz on 2006-08-04
On the top right of my screen theres a little red/white box and when i highlight it it says 

"A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was:'Error: BrokenCount > 0'

Can someone help me out please?

---

### Post by Tomosaur on 2006-08-04
Sounds like your system is having trouble updating your software. Try opening up a terminal and typing the following line:

'sudo apt-get update'

If all goes well it will update your applications list and the available applications from the internet. If it doesn't work, paste whatever it says on here, maybe someone can help.

There seem to be a lot of repository problems lately, I'm assuming the servers are playing up.

---

### Post by ifokkema on 2006-08-04
> **Tomosaur said:**
> 
'sudo apt-get update'

Actually, apt-get update will just download the latest package lists from the server. It will not fix this problem...
Try
```
sudo apt-get update
sudo apt-get install -f
```
To see what's up.
apt-get install -f will, according to the manual: "attempt to correct a system with broken dependencies in place".

---

