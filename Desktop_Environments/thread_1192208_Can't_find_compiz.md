---
title: "Can't find compiz"
date: 2009-06-19
forum: Desktop Environments
---

### Post by prions on 2009-06-19
I installed everything, but can't find the location anywhere. 

It's not in system>preferences. 

Also, when I run it from the Add/Remove applications manager, it brings me to a page where it says I have to install compiz. 

When I click install, it says I already have it installed.

---

### Post by neu2buntu on 2009-06-19
you probably need the manager installed. open the terminal >applications>accessories>terminal and type command ```
ccsm
``` followed by enter/return, if the compiz manager is not installed you will get a message about installing it,

---

### Post by raymondh on 2009-06-19
> **prions said:**
> I installed everything, but can't find the location anywhere. 

It's not in system>preferences. 

Also, when I run it from the Add/Remove applications manager, it brings me to a page where it says I have to install compiz. 

When I click install, it says I already have it installed.

Hi,

I am assuming you've installed ccsm (compiz-config-settings-manager) and the necessary drivers for your hardware are installed.

RT. click your desktop > change desktop background > visual effects and set to EXTRA

Access your ccsm (system > preferences) and compiz away.

[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

Happy Ubuntu-ing.

---

### Post by prions on 2009-06-19
```
ubuntu@ubuntu:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
You will have to enable the component called 'universe'
bash: ccsm: command not found
ubuntu@ubuntu:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
ubuntu@ubuntu:~$ 
```

Hmm?

I have been having driver problems, so I think its that.

---

### Post by neu2buntu on 2009-06-19
that will probably not be the case...as your error msg said "enable universe" repo.  goto >system>administration>software sources....and in the "ubuntu software " tab tick on "universe" (you may also have to do code ```
sudo apt-get update
``` also then open the terminal again and type ```
sudo apt-get install compizconfig-settings-manager

```after installation i think ccsm(compiz-config-settings-manager) will be in >system>prefs/admin...if not just do code in terminal ```
ccsm
```compiz works on a hotkey basis....eg for "cube" you will press keys [shift+alt+left_mouse_key] or something like that......ccsm will show you the hotkeys for this or alternatively you can set your own,



i just installed it again myself so the compiz config settings manager in in >system>preferences....have got my wobbly windows now...lol

---

### Post by prions on 2009-06-20
Fixed! Thank you. :D

---

