---
title: "Store password of ssh key in gnome keyring"
date: 2009-05-01
forum: General Help
---

### Post by helino on 2009-05-01
Hi,

when I used Ubuntu 8.10 I was able to store my sshkeys passphrase in gnome-keyring, and then it was automatically unlocked when I logged in. 

However, in Ubuntu 9.04, this doesn't seem to work? In Ubuntu 8.10, GNOME simply asked if I wanted to stored the passphrase of the sshkey in the keyring the first time I used, but this doesn't work with 9.04.

Have anyone else had this problem?

I'm grateful for any help

---

### Post by Hund on 2009-05-03
I have the same problem. :( I tried to remove all the settings but that didnt help at all.

---

### Post by frafu on 2009-05-05
Same problem here on one of my ubuntu 9.04 installation. :-(

I compared the installed packages (searching for ssh, gnupg, gpg in synaptic) and they seem to be same. Now I wonder whether there might be a difference in the configuration files.  :-/

Anybody knows where to look?

Cheers

---

### Post by frafu on 2009-05-05
Hello, 

I Just found the problem on my installation where it was not working: the gnome-keyring-daemon was disabled under the menu System->Preferences->Startup Applications. 

Cheers 

Francesco

---

### Post by helino on 2009-05-06
> **frafu said:**
> Hello, 

I Just found the problem on my installation where it was not working: the gnome-keyring-daemon was disabled under the menu System->Preferences->Startup Applications. 

Cheers 

Francesco

Hi Francesco, thanks for your time and for looking into this problem.
Unfortunately for me, gnome-keyring-daemon is checked under Startup Applications, so it's not disable for me :(

Anyone else have any suggestions on how to solve this?

---

### Post by vincenma on 2009-05-07
Hello, I think I have the same problem...

keyring worked with 8.10, but stopped working in 9.04 :(

Upon openning a terminal to ssh to a foreign host, I used to be asked once for my keyring passphrase...then all subsequent openning a terminal to ssh were passwordless. 

Now, every time I start a terminal and try to ssh, I get asked for the keyring passphrase...

any ideas any one?

---

### Post by gravyboat on 2009-05-10
I can confirm the same problem.  In Ubuntu 9.04 I can't seem to find a way to have my private SSH key unlocked automatically once I've logged in.  This feature was great in Ubuntu 8.10 and a real bummer it appears to no longer work.

---

### Post by helino on 2009-05-15
Is this a bug? A lot of people seems to have this problem...If so, should I file a bugreport somewhere?

---

### Post by Brandon Williams on 2009-05-15
I don't know whether this is a bug in gnome-keyring, since I don't use that functionality of the keyring. However, if it is a bug and no-one else can come up with a work-around that is specific to gnome-keyring, then you could try using my [ssh-askpass-keyring](https://launchpad.net/ssh-askpass-keyring) utility as a short-term work-around while you wait for the gnome-keyring bug to get fixed. Click 'External Downloads' to get to my PPA. The Intrepid version works just fine on Jaunty.

I don't normally recommend switching to my utility unless your needs aren't met by the functionality already built in to the keyring. For me, that's true because the keyring doesn't store passphrases for SSHv1 keys, and that's what my company uses. You might want to use my utility while you wait for a bug fix, but I recommend going back to the gnome-keyring's built-in functionality once it's back in working order. After all, there's no need for two programs when one will do.

---

### Post by akaihola on 2009-05-28
I've been fighting with this issue as well, and the most frustrating thing is that I can't find good user documentation for the GNOME keyring. A clear explanation of the whole system in layman terms would be necessary to be able to really use the user interface and not just try everything blindly.

---

### Post by helino on 2009-06-06
On which bugtracker should I post this a bug? I've never posted bugs in an open-source project before, so it would be nice if someone could point me in the right direction :)

---

### Post by Brandon Williams on 2009-06-06
You could report the bug [in launchpad](https://bugs.launchpad.net/ubuntu/jaunty/+source/gnome-keyring/+bugs), or go straight to the [gnome bugzilla page](http://bugzilla.gnome.org/).

---

### Post by helino on 2009-06-09
Hi Brandon, thanks for your help. I reported the bug on launchpad, since it seems like an ubuntu issue when it worked in previous versions. Once again, thanks for your help and time!

---

### Post by vincenma on 2009-06-09
> ...then you could try using my ssh-askpass-keyring utility as a short-term...

Hello Brandon,

thanks for your utility :) I will use it while waiting for the bug fix.

thx again!

---

### Post by helino on 2009-06-18
I reported the bug on launchpad here: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/385331](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/385331)

If you suffer from the bug, please reproduce it and confirm it by writing a comment on the launchpad page.

Please help out with testing if the devs needs it, this way the problem might get solved.

---

