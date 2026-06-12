---
title: "Installing Flash Player?"
date: 2008-12-19
forum: General Help
---

### Post by nielscase on 2008-12-19
So I started installing it on my own so I could try to learn a little more about linux. I got about halfway through and got stuck and was going to finish the next day then when I was using firefox it poped up something saying it would install the flash player for me so I tried it and here is my problem.

When I try and install with the update manager it says: You have 1 broken package on your system!

Use the "Broken" filter to locate it.

and then says: E: /var/cache/apt/archives/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

also when I try to fix the broken package with the synaptic package manager it says the same thing.

I have tried to force overwrite but I'm not sure if I am doing it properly.

---

### Post by Tomatz on 2008-12-19
Try this:

```
sudo apt-get autoclean

sudo apt-get update
```

Then try ;)

---

### Post by nielscase on 2008-12-19
It didn't work, same error msg as before.

---

### Post by Tomatz on 2008-12-19
Hmmm give this a try:
```

aptitude remove nspluginwrapper
apt-get update
apt-get upgrade

```
Reboot

Then install nspluginwrapper ;)

---

### Post by nielscase on 2008-12-19
That does not work either.

---

### Post by 1467 on 2008-12-19
```
sudo killall apt-get
```

```
sudo apt-get autoremove
```

---

### Post by nielscase on 2008-12-19
I thought that was going to do the trick but it didn't, does it matter if I restart or not after the autoremove?

---

### Post by Tomatz on 2008-12-19
Is your install a x86 64 or an i386?

---

### Post by nielscase on 2008-12-19
Well I have a intel core 2 duo processor but I think it may have installed as x86 64, how can i check?  I just cant get anything to work to remove the nspluggin wrapper.

---

### Post by nielscase on 2008-12-19
> **nielscase said:**
> So I started installing it on my own so I could try to learn a little more about linux. I got about halfway through and got stuck and was going to finish the next day. 

I just used some alien app or something I think to install the nspluggin, I cant find the guide I was using to do it with otherwise I would post the link.

---

### Post by nielscase on 2008-12-19
dpkg -i --force-overwrite /var/cache/apt/archives/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb

worked

---

