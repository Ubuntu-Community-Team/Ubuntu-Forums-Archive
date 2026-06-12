---
title: "[SOLVED] Repair Ubuntu"
date: 2007-07-26
forum: Desktop Environments
---

### Post by MacDuff on 2007-07-26
I have a problem with the Synaptic package manager of Ubuntu 7.04.  A package won't install and I can not clear it from the manager.  Is there a way to repair Ubuntu from the install DVD or can I delete some file(s) so that I can get the the Synaptic pkg manager working again?

Thanks

---

### Post by aysiu on 2007-07-27
Close Synaptic.

Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get -f install
``` and then paste the output back here.

---

### Post by MacDuff on 2007-07-27
Here is the output you requested:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mailwasher needs to be reinstalled, but I can't find an archive for it.

---

### Post by aysiu on 2007-07-27
Can you try pasting this command in? ```
sudo dpkg --remove --force-remove-reinstreq mailwasher
```

---

### Post by MacDuff on 2007-07-27
Here is the result:

macduff@macduff-laptop:~$ Reading package lists... Done
bash: Reading: command not found
macduff@macduff-laptop:~$ Building dependency tree       
bash: Building: command not found
macduff@macduff-laptop:~$ Reading state information... Done
bash: Reading: command not found
macduff@macduff-laptop:~$ E: The package mailwasher needs to be reinstalled, but I can't find an archive for it.

Still cannot run Synaptic Pkg Manager without getting the error message.

---

### Post by OzzyFrank on 2007-08-11
Remember for future reference that while Synaptic is sorta "stuck" it isn't actually the problem, but the program that is listed in the error. Ideally, package managers should be able to workaround packages that didn't install properly, and for the most part they do. Sometimes a package keeps trying to install unsuccessfully, and this can halt progress till you find and remove it (mark for Complete Removal).

---

### Post by MacDuff on 2007-08-12
> **aysiu said:**
> Can you try pasting this command in? ```
sudo dpkg --remove --force-remove-reinstreq mailwasher
```
Thanks OzzyFrank:

I am reviewing the replies to my previous threads and found this one after I checked your other reply.

As you will note from the ealier posts, I did try your suggestion soon after you made it but it did not appear to work.

I just re-tried it again and after some time, and a number of messages which seemed to indicate to me that the command was not working or could not execute the command, I finally received a message that Mailwasher was removed.  Perhaps I did not wait long enough the first time I tried.

That is great that there is actually a way to remove corrupted applications without having to re-install the OS.  Another big PLUS for Linux/Ubuntu!

I just wish there was a reference guide that I could get that would tell me how to find those commands.  At the time I decided to give Ubuntu a try I purchased  "Ubuntu Hacks" and Ubuntu for Non-Geeks".  They are good introductory stuff but I need a bible which has the more obscure answers to problems that may be encountered.  It must have a good index.  Do you know of such a publication?

Now if I can get an answer to my networking problem(s), I will be very much happier.  I will spend some time on that today.

I guess I should not have tried to install Ubuntu on more than one system until I had learned more about it.  Trying to trouble-shoot a couple of machines each with different problems at the same time I am writing and testing code for the "other" world is a tad too stressful.

Your assistance is very much appreciated.

Mac

---

