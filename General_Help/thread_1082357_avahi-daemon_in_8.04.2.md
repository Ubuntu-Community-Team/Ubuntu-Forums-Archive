---
title: "avahi-daemon in 8.04.2"
date: 2009-02-27
forum: General Help
---

### Post by ajgreeny on 2009-02-27
I have stupidly stopped the avahi-daemon from starting at boot up and now am having several problems with *pulse-audio device chooser* which will not start unless i manually start the avahi-daemon.
Now I can not seem to get the avahi-daemon to start at boot time again, as it is not listed in boot-up-manager (bum) or System>Administration>Services.   I guess I must have removed its listing in one of these utilities, though I don't remember doing so.  How can I make sure that it starts at boot up in future?

---

### Post by Yellow Pasque on 2009-02-27
The easy way would be to reinstall the avahi-daemon package
```
sudo apt-get --reinstall install avahi-daemon
```

---

### Post by ajgreeny on 2009-02-27
Thanks, Temujin, but immediately after asking the question I did more or less that, though I completely removed it with synaptic and then reinstalled it.  It removed one or two other packages which I also reinstalled and now all is well again.

---

