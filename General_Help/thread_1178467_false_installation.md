---
title: "false installation"
date: 2009-06-04
forum: General Help
---

### Post by stonebit on 2009-06-04
After some updates ran, evolution would not start. I have restarted several times and removed and installed evolution several times. When attempting to run from shell, the simple message is:

bill@stone:~$ evolution
The program 'evolution' is currently not installed.  You can install it by typing:
sudo apt-get install evolution
bash: evolution: command not found

Evolution *IS* installed!
I also tried searching in /bin and usr/bin for evolution (and everywhere else). I cannot find it anywhere on my drive. The install runs successfully, but it's like the program is not actually being installed.

Any ideas?

---

### Post by nikgare on 2009-06-04
what happens when you type:

**sudo apt-get install evolution**

---

### Post by stonebit on 2009-06-05
I figured it out: my /var/lib/dpkg/status file is corrupted to no end. It's broken. I think it's my hard drive. I've found evidence of some other evidence of corruption as well: some files do not check out when md5sums are used against them.

---

