---
title: "Apt-get broken"
date: 2005-12-15
forum: General Help
---

### Post by IYY on 2005-12-15
I was playing around with dselect and somehow lost the ability to add packages via apt-get, synaptic or anything else. The error that I get is this:

[B]ilya@floyd:~$ sudo apt-get install dillo
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: The list of sources could not be read.[/B]

What's wrong, and how do I fix it?

---

### Post by aysiu on 2005-12-15
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by cstudent on 2005-12-15
Sounds like your sources.list is messed up. You can use Nautilus to browse up through the folders to /etc/apt/ and see if your sources.list file is still there. If not a workable solution could be to download the Automatix script and extract it. There is a sources.list included with it. You could copy it to your /etc/apt/ directory, but you need to remember to do it as root.

---

