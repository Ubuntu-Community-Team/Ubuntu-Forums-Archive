---
title: "System settings: must run as root/&quot;administrator&quot;(?)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jaspeers on 2005-10-13
To change certain settings in the System Settings menus, Kubuntu says I have to run in administrator mode.  It prompts me for a password via kdesu, which I provide, briefly outlines everything in red, then immediately goes back to where it was, with all the options greyed out.

No errors are given.  I hope I'm not being an airhead here, but what am I missing?  My google search was fruitless...

---

### Post by mlomker on 2005-10-13
That was a common problem in older versions of Breezy.  Have you updated recently?

A work around is to launch kcontrol from the Run Command line using **kdesu kcontrol**

---

### Post by jaspeers on 2005-10-13
Hmmm... I just did a dist-upgrade today and it's still happening for me.

For now I'll go with running control center as root, but I'd still like to figure out what my problem is.

---

### Post by z_pod on 2005-10-14
I can confirm new setting manager works properly with kubuntu breezy release Live (no root/admin issue).

Hmm...both network profiles and partition mounter work. Gggreat job guys !

BTW Kubuntu live CD is faasssst, faassst OMG it's faasst !!!!

Best Regards

---

### Post by elefthera on 2005-10-14
[QUOTE=z_pod]I can confirm new setting manager works properly with kubuntu breezy release Live (no root/admin issue).[/QUOTE]
Not for me it doesn't... also, "kdesu kcontrol" accepts the password, then zilch...

Hmmm... Didn't have these probs under Gnome...

---

### Post by Lausi on 2005-10-26
I have the same problem since I updated from the bug with the USB-Sticks-mounting... There is no possibility at the moment?

Lausi

---

### Post by deeek on 2005-10-28
I just wanted to chime in and say that I have been having the same problem.  I hopt this can be resolved, it is quite annoying.

---

