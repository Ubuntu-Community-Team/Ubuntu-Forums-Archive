---
title: "how to restart a startup script process"
date: 2009-02-15
forum: General Help
---

### Post by super_czar on 2009-02-15
I use a EV-DO dial up connection on my unattended ubuntu home server which is automatically started at reboot/resume after power outage via a startup script

```
#!/bin/bash
wvdial
```
 sometimes, the EV-DO connection slows down, which can usually be fixed by a reconnect

Now normally, I would just do a ctrl C to elegantly stop the wvdial process terminal window
However, I am not sure how to do the same on a startup script process

(other than the brute method of ps -A | grep wvdial to find the pid for wvdial and then kill it)

A *stop wvdial* returns an unknown job error
any pointers?

---

### Post by super_czar on 2009-02-17
bump-- up up up you go!

---

### Post by caljohnsmith on 2009-02-17
So where did you put the start up script? If you installed it to one of the runlevel directories with the "update-rc.d" command, you can probably stop the service via:
```
sudo /etc/init.d/wvdial stop
```
Or whatever is the name of the script/service. Is that maybe what you are looking for?

---

### Post by super_czar on 2009-02-19
actually I toook the easy way out.
I created the script, then added it to the startup items for my Login o through the Gnome control panel

---

