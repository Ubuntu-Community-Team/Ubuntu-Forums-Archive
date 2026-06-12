---
title: "Add/Remove my soul"
date: 2006-09-30
forum: Desktop Environments
---

### Post by OptimusPrime on 2006-09-30
This is bad, really bad.  When I open Add/Remove this pops up:
Failed to check for installed and available applications
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
What is going on?!:confused:

---

### Post by BoneKracker on 2006-09-30
What happens when you do what it said?  (I.e., go to the terminal and type in:```

sudo apt-get update
```

Also, while you're in there:
```
ls -l /etc/apt/sources.lst
```
(paste the output in a reply)
```
cat /etc/apt/sources.lst
```
(paste the output in a reply)

I may not still be up, but that will help somebody answer your question.

---

### Post by jpkotta on 2006-09-30
It's not that bad.

Do what it says```
sudo apt-get update
```If you're sources.list file is bad, it will tell you what line the problem is at.  If it's not bad, then we'll know the problem is somewhere else.

---

