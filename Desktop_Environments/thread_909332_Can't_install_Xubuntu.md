---
title: "Can't install Xubuntu?"
date: 2008-09-03
forum: Desktop Environments
---

### Post by kaldor on 2008-09-03
I had to do a system reformat, and now I want to install the Xubuntu desktop. My OS is currently Ubuntu 8.04

last time, all I did was sudo apt-get install xubuntu-desktop.

Here is what happens now:

```
michael@laptop:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xubuntu-desktop

```

How can I fix this?

---

### Post by snowpine on 2008-09-03
Can you please try 'sudo apt-get update' and post the output here if there are any error messages?

---

### Post by kaldor on 2008-09-03
```
michael@laptop:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_CA
Hit http://wine.budgetdedicated.com hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_CA
Hit http://archive.ubuntu.com hardy Release    
Hit http://wine.budgetdedicated.com hardy Release
Hit http://archive.ubuntu.com hardy/main Packages
Ign http://wine.budgetdedicated.com hardy/main Packages
Hit http://wine.budgetdedicated.com hardy/main Packages
Reading package lists... Done

```

---

### Post by kaldor on 2008-09-03
Anyone want to help me with this still? =Þ

---

### Post by sayakb on 2008-09-03
It seems like you don't have your repos enabled. Here's a simple way for doing it:
Goto System->Administration->Software Sources
Under the *Ubuntu Software* tab, **check** the first 4 boxes.
Under the *Updates* tab, **check** the first two boxes (ie. Important and recommended updates)
Under the *3rd party software* tab, check all available options.
Press Close button and press **Reload** button when prompted to. Now try to install the package again.

---

### Post by kaldor on 2008-09-03
Thanks, mate! This helped a lot :)

---

### Post by sayakb on 2008-09-03
Glad I could help! :)
If your problem has been solved, please mark the thread as *Solved* (Thread tools->Mark thread as solved)

---

