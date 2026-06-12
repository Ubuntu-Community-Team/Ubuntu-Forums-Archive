---
title: "Skype does nothing"
date: 2009-03-07
forum: General Help
---

### Post by herbig on 2009-03-07
I'm trying to get Skype working in Intrepid.  When I click the icon, nothing happens.  When I type skype in the terminal, nothing happens, and no error is generated.

I've tried absolutely everything that Google and these forums has to offer on this, to no avail.  I've installed using synaptic and downloaded the deb, both the same.  There's nothing running in the System Monitor either.

Any help would be greatly appreciated...

---

### Post by kestrel1 on 2009-03-07
Have you tried removing Skype, downloading the latest (I would assume you had already done that) & re-installing.
You can remove skype, via Synaptic Package Manager or typing the following in a terminal:```
sudo apt-get remove skype
```
EDIT
You could do a purge on the removal with the following:```
sudo apt-get remove --purge skype
```

---

### Post by HermanAB on 2009-03-07
Some programs check to see whether they are already running in order to avoid accidentally running multiple instances of the same thing.  Sometimes, this causes a problem.  Display the processes with 'ps -e' and look for skype.  If it is already listed, but dead, 'kill -9' it to get rid of it, then try running it again.

When all else fails, download the 'static' version of Skype from the Skype web site.  It has all required libraries linked in and should 'Just Work'.  I'm using that version on my little Eee PC and even the camera works.

Cheers,

Herman

---

### Post by herbig on 2009-03-08
I have uninstalled, and downloaded the deb.  Tried installing through synaptic as well.  There are no skype processes running in the System Monitor.  Basically when I click the Skype icon or type Skype, nothing happens at all.  No error, no process appears, nothing.

---

