---
title: "terminal installation problems"
date: 2009-04-14
forum: General Help
---

### Post by Alexm21 on 2009-04-14
hey,

Whenever I try to install a progrm such as wine or compizconfig-settings-manager through sudo apt-get install wine or sudo apt-get install compizconfig-settings-manager, it always says

alex@alex-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
alex@alex-laptop:~$ 
 
does anybody have any idea as to what I can do to fix this?

btw: i'm using ubuntu 9.04 beta if that helps any.

---

### Post by stumbleUpon on 2009-04-14
compizconfig-settings-manager is in the universe repositories. If you have not enabled them, try doing that first and see.

---

### Post by soltanis on 2009-04-14
Strange. Have you tried

```

sudo apt-get update

# then

sudo apt-cache search wine

```

? What's the output of the second command?

---

### Post by maheshasolkar on 2009-04-14
compizconfig-settings-manager is a part of 'universe' repository. Have you enabled the universe repository in Synaptic? If not, you can do so by following these steps:

Open Synaptic Package Manager from *System -> Administratio*n menu.

In Synaptic, open *Settings -> Repositories*. In there, check the checkbox that says *Community-maintained Open Source software (universe)*.

Then try:

```

  sudo apt-get update
  sudo apt-get install compizconfig-settings-manager

```

Hope this helps.

---

### Post by Alexm21 on 2009-04-14
> **maheshasolkar said:**
> compizconfig-settings-manager is a part of 'universe' repository. Have you enabled the universe repository in Synaptic? If not, you can do so by following these steps:

Open Synaptic Package Manager from *System -> Administratio*n menu.

In Synaptic, open *Settings -> Repositories*. In there, check the checkbox that says *Community-maintained Open Source software (universe)*.

Then try:

```

  sudo apt-get update
  sudo apt-get install compizconfig-settings-manager

```


Hope this helps.

Yes it works! Thank you very much!!

---

