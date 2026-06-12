---
title: "sudo skype etc"
date: 2009-04-04
forum: General Help
---

### Post by msivaraman on 2009-04-04
i am new to ubuntu.
i recd. and installed ubuntu 8.10 desk top edition.
i want to know how to set up sudo?
i want to know how to set up skype?
i want to know how to set up tamil fonts?
thanks
 msivaraman

---

### Post by cariboo on 2009-04-04
> i want to know how to set up sudo?

You don't need to change any sudo seetings, it is set up for your user by default. If you need to run a command as root, graphically press Alt-F2 and type:

```
gksu nautilus
```

The above command will start the file manager as root.

> i want to know how to set up skype?

To install skype, you need to enable the [Medibuntu]("http:///help.ubuntu.com/community/Medibuntu") repositories, Just follow the instructions for your version. Make sure you scroll down and set up the gpg keys. Once you have the repositories enabled, use Add/Remove Programs or Synaptic Package Manager to install skype.

> i want to know how to set up tamil fonts?

Have a look at [this]("http:///www.linuxquestions.org/questions/ubuntu-63/tamil-fonts-installation-in-ubuntu-560448/") to install Tamil fonts. It is for an older version of Ubuntu, but it should work.

Jim

---

