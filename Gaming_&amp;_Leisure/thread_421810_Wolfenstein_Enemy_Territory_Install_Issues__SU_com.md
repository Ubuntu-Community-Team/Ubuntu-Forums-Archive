---
title: "Wolfenstein Enemy Territory Install Issues / SU command?"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by thisdevil on 2007-04-24
First off I am new to Linux, thanks for your patience

I am trying to install Wolfenstein Enemy Territory, I had run into afew problems that I found answers to here on the forums. Such as Installer Version, learning terminal commands, navigating to dir and so on. From reading posts on different sites it seems that everyone is able to get the game to install using the following...

su
"your p*****word"
chmod u+x et-linux-insertnameinfo
./et-linux-insertnameinfo

the one thing here I can't do is the su command? I enter my password and it rejects every time... I can get the installer to open/run but when it goes to install to a directory it says it doesn't have permission to place files in that directory. I feel like this is linked back to the su command... Please if some one can shed some light on this I would appreciate it.

---

### Post by sisco311 on 2007-04-24
> su
"your p*****word"
chmod u+x et-linux-insertnameinfo
try
```
sudo chmod u+x et-linux-insertnameinfo
```

---

### Post by sisco311 on 2007-04-24
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by thisdevil on 2007-04-24
I now used the command line

sudo chmod u+x et-linux-insertnameinfo

i typed my password and it gave me a new black "user@computer/dir" type line

i followed up with 

./et-linux-insertnameinfo

program started to run I okayed my way to the point where it told me this...

Failed permissions
No write permission to /usr/local/games

and now I am stuck here, anything for me?

---

### Post by DoktorSeven on 2007-04-24
sudo chmod u+x ./et-linux*
sudo ./et-linux-whatever 
(type out the full name of the executable or hit TAB to autocomplete it)

---

### Post by thisdevil on 2007-04-24
Thank you both for you help, anyone using this post as a reference for solving the same problem, make sure you have the newest version of ET I has used et-linux-2.60.x86.run then follow DoktorSeven's instructions they fixed my install issue.

---

