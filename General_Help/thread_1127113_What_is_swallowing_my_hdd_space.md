---
title: "What is swallowing my hdd space"
date: 2009-04-16
forum: General Help
---

### Post by happyhacker on 2009-04-16
I use webmin to access our server via the network. I have used up 21Gb of the 36Gb available. If I open the file manager it only tells me that each folder is 4Kb in size. How do I find out the storage used on all my folders? I suspect it's related to client backups but need to pin it down before I take action.

---

### Post by benj1 on 2009-04-16
what program are you using?
there disk usage analyser (GUI)

or du for the terminal

---

### Post by happyhacker on 2009-04-16
Thanks I used du and found that backups are taking up 18Gb, so that's the culprit. What is the du cmd to just get the first level of directories below the home folder? If I do "du /home" I get the lot!

Is there a webmin module for this?

---

### Post by uncle-c on 2009-04-16
Look in /var/cache/apt 
Do you have a lot of .deb files ; software packages which you downloaded and were installed on your system ? Use

```


$ sudo apt-get clean


```

to clear unwanted software packages

---

### Post by PACSFerret on 2009-04-16
du --max-depth=1

---

