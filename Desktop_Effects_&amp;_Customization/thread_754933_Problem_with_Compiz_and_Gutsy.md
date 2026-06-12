---
title: "Problem with Compiz and Gutsy"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by tsbaker on 2008-04-14
tyler@tyler-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
 
Every forum I've read says all I need to do is install the compiz settins manager which I did. It then says an Advanced Desktop settings something or another should should up under preferences which it does not. I get the Compiz settings manager. However when I click on it, it does not launch. nor does running cssm in the terminal work either. 

any suggestions????

thanks for any help that can be offered

---

### Post by Zorael on 2008-04-14
Did you upgrade from Feisty?

If you did, you likely have remnants from previous installations left in your system, *especially* if you used third-party eyecandy repositories. Check your Software Sources (alternatively /etc/apt/sources.list and files in /etc/apt/sources.list.d/). A common "bandit" is Treviños' eyecandy Feisty repository, but there are certainly others. Disable them or comment them out, then enter the following in a terminal:

```
$ sudo apt-get autoremove --purge compiz* libcompiz* libdeco* beryl* libberyl* emerald* libemerald*
$ sudo apt-get clean
$ sudo apt-get update
```

Then reinstall Compiz (and Emerald), either through a graphical package manager such as Add/Remove Programs, Synaptic or Adept Manager, or via the terminal. Don't forget the compizconfig-settings-manager package.


If you have a fresh Gutsy install, are you using the Compiz version available from the official repositories, or are you running a git installation? Or perhaps from some other, third-party repository?

---

### Post by tommyhakinen on 2008-04-14
to install compiz fusion from terminal use this:

> 
sudo apt-get install compizconfig-settings-manager


to run it, press alt + F2 then enter this:

> 
compiz --replace


hope this can help

---

