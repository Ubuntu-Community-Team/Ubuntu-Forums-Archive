---
title: "Error: &quot;evolution-2.6 has quit unexpectedly&quot;"
date: 2007-03-01
forum: Desktop Environments
---

### Post by Graybeard on 2007-03-01
Everything had been working fine for months. Then I installed libccid and two dependencies, libpcsclite1 and pcscd from synaptic package manager. They didn't do what I wanted and I uninstalled them with synaptic package manager. And then, loading evolution produces the error message "evolution-2.6 has quit unexpectedly." 

I reinstalled evolution and got the same result.

I reinstalled libccid etc. and got the same result.

Questions:
1. Can I recover without losing saved mail, and if so how?
2. If I can't, and have to reinstall everything including Ubuntu, where in the file system is mail stored and how can I back it up in a way that will allow me to merge it back into the newly installed system?

FYI, I'm running 6.06 LTS fully updated on a Dell 4550


[B][I]Note: the fix from other threads;
cd /usr/lib
sudo ln -s firefox/libfreebl3.so
does not remedy the problem I'm having[/I][/B]

---

### Post by edu65 on 2007-03-01
> **Graybeard said:**
> 

Questions:
1. Can I recover without losing saved mail, and if so how?
2. If I can't, and have to reinstall everything including Ubuntu, where in the file system is mail stored and how can I back it up in a way that will allow me to merge it back into the newly installed system?



Evolution keeps your mail, calendar data, etc. in the hidden directory ".evolution", under your home directory. Back up that directory somewhere else if you decide to reinstall. Sorry I can't be more helpful concerning your problem.

---

### Post by Graybeard on 2007-03-02
Thanks, edu65.  Today's update of yesterday's update has fixed the evolution problem but knowing where all the data is kept is good information. I've now backed it up to another computer.

---

### Post by tlimon on 2007-03-02
I have the same problem.  After I renamed the .evolution folder to .evolution-backup, the error is gone.  Evolution works fine now, so there must be something in that folder that is causing the error. 

Anyone know how to import items from the backup folder into evolution? Do I just start copying things back into the .evolution folder one-by-one until it bombs again?

---

### Post by la3875 on 2007-03-03
I had same problem recently and was starting to panic. I have no advice on backing up the file but did get it running again after finding this thread: 
[https://launchpad.net/products/evolution/+bug/56118](https://launchpad.net/products/evolution/+bug/56118)

Appears the issue is related to Firefox upgrade. I used update manager to get most current Firefox upgrade and Evolution is back!

All the best!

---

