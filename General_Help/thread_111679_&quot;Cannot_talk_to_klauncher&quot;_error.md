---
title: "&quot;Cannot talk to klauncher&quot; error"
date: 2006-01-02
forum: General Help
---

### Post by Seth Williamson on 2006-01-02
I have started to get an odd error when I log out of Kubuntu.  I briefly see an error message that says "Cannot talk to klauncher."

Can somebody tell me what this means and what I need to do to get rid of it?


Seth Williamson
Slings Gap
Franklin County, VA
USA

---

### Post by garba on 2006-01-02
yes, that's a very well known bug and it hasn't been solved yet, the only thing you can do is bear with it :(

---

### Post by Dencrypt on 2008-01-26
Open up a terminal and do:

```
dcopserver_shutdown
kdeinit
```

Not a permanent solution but it takes the problems away temporarily untill you restart or closes X.

---

### Post by caughran on 2008-02-22
> **Dencrypt said:**
> Open up a terminal and do:

```
dcopserver_shutdown
kdeinit
```

Not a permanent solution but it takes the problems away temporarily untill you restart or closes X.

I tried this; it tells me, "kdeinit: Communication error with launcher. Exiting!"

And the application still won't add a file.

---

### Post by p_quarles on 2008-02-22
Old bug, and one that likely won't be fixed given the focus on KDE 4.

When I encounter this, I just restart KDM manually, which almost always fixes the problem. Ctrl-alt-F1 to open the TTY console, then:
```
sudo /etc/init.d/kdm restart
```

---

### Post by caughran on 2008-02-22
> **p_quarles said:**
> Old bug, and one that likely won't be fixed given the focus on KDE 4.

When I encounter this, I just restart KDM manually, which almost always fixes the problem. Ctrl-alt-F1 to open the TTY console, then:
```
sudo /etc/init.d/kdm restart
```

Thanks. It tells me, reasonably enough, that KDM is not my default display manager.

Is there a KDE4 klauncher that works better? Should I tear out every shred of kde, and install -- what?

I synchonize the palm pilot to Kontact; it has worked well for about 6 months. Lately, it won't accept palm file installs because of the klauncher error. Kpilot does not accept drag and drop, nor will it accept a file with full address given.

---

### Post by p_quarles on 2008-02-22
> **caughran said:**
> Thanks. It tells me, reasonably enough, that KDM is not my default display manager.

Is there a KDE4 klauncher that works better? Should I tear out every shred of kde, and install -- what?

I synchonize the palm pilot to Kontact; it has worked well for about 6 months. Lately, it won't accept palm file installs because of the klauncher error. Kpilot does not accept drag and drop, nor will it accept a file with full address given.
No, the login manager in KDE 4 is currently pretty unstable. Last I heard, it was broken altogether, but this may have changed by now.

In any case, the error message you got can be approached in a couple ways. Restart the display manager that *is* the default:
```
sudo /etc/init.d/gdm restart
```
Or, make kdm the default:
```
sudo dpkg-reconfigure kdm
```

---

