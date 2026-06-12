---
title: "Issues installing Wine on a Dell inspiron 9300"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by drfarrin on 2008-03-27
ok, to avoid being bombarded with replies saying "lurk more, you should find a solution that way" or other things to the same effect, I did look around and haven't seen a solution to my problem.

(newb sauce here)

so I installed 7.10 on my dell inspiron 9300 and I also checked to make sure the disc wasn't corrupted (ran the little program that checks prior to installation). I would like to install Wine on this laptop so I started mucking about and found this: [http://ubuntuforums.org/showthread.php?t=736816](http://ubuntuforums.org/showthread.php?t=736816)

which was helpful, I can see it in the list on the synaptic package manager, I have "wine" and "wine-dev" to check, now here's the problem: when I click the boxes to install them they give me errors.
-------------------------

I click on wine and it says: the following packages have unresolved dependcies. Make surethat all required repositories are added and enabled in the preferences.

wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable

---------------------------

I click on wine-dev and the error that pops up says: the chosen action also affects other packages. The following changes are required in order to proceed.

To be installed: 

libc6-dev
linux-libc-dev

---------------------------

when I tried to install "libc6-dev" it told I couldn't because it was dependent on wine and wine wasn't going to be installed.


So I ask you, what does this mean and how can I fix this?

your friendly neighborhood Dr Farrin

---

### Post by gbrainin on 2008-03-27
Try using the Add/Remove Programs tool (Applications -> Add/Remove...) instead of the package manager.

---

### Post by drfarrin on 2008-03-28
thanks It works now

---

