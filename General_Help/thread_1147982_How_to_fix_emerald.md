---
title: "How to fix emerald?"
date: 2009-05-03
forum: General Help
---

### Post by techphets on 2009-05-03
Hi, 

I installed Emerald and it seemed to work fine.  I wanted to ensure I knew how to stop/start it and the only method I found was to uninstall it. 

I ran apt-get remove emerald and it uninstalled.  One of my effects went with it (exploding feature for closing windows).  I reinstalled emerald but it does not seem to work. 

I've tried typing "emerald --replace" at a terminal but the terminal never returns to the shell prompt as it did the first time.  Instead the command runs until interrupted (I let it sit for over an hour).  I've tried selecting different themes in Emerald but nothing changes. 

Any ideas?

---

### Post by lovinglinux on 2009-05-04
> **techphets said:**
> Hi, 

I installed Emerald and it seemed to work fine.  I wanted to ensure I knew how to stop/start it and the only method I found was to uninstall it. 

You should use *metacity --replace* or install [fusion-icon](http://ubuntuforums.org/showthread.php?t=809695) or [Compiz Switch](http://ubuntuforums.org/showthread.php?t=662926) to easily toggle between Emerald and other window managers.


> **techphets said:**
> I ran apt-get remove emerald and it uninstalled.  One of my effects went with it (exploding feature for closing windows).  I reinstalled emerald but it does not seem to work. 

I've tried typing "emerald --replace" at a terminal but the terminal never returns to the shell prompt as it did the first time.  Instead the command runs until interrupted (I let it sit for over an hour).  I've tried selecting different themes in Emerald but nothing changes. 

Any ideas?

Check if you still have libemeraldengine0

```
sudo apt-get install libemeraldengine0
```

---

### Post by soro2005 on 2009-05-04
> **techphets said:**
> I've tried typing "emerald --replace" at a terminal but the terminal never returns to the shell prompt as it did the first time.  Instead the command runs until interrupted (I let it sit for over an hour).  I've tried selecting different themes in Emerald but nothing changes.

It doesn't return to the prompt until the process is terminated. The process is not terminated until emerald is shut down. Thus, the prompt not returning is not a bad sign. To decouple the process from the terminal, start it with
```
emerald --replace &
```
It'll probably write some output the terminal until you shut the terminal window. That's normal. Better, use Compiz Fusion Icon.

---

