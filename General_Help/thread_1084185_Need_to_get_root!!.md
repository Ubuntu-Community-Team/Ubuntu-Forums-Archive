---
title: "Need to get root!!"
date: 2009-03-01
forum: General Help
---

### Post by freakinjonathan on 2009-03-01
ok so I completely f'd up the permissions in my ubuntu computer. It wouldn't even load up gnome or anything. I popped in the live CD and chmodded the whole drive as readable and writable by anybody. That was able to start up gnome. Now i get the error

```

Users $HOME/.dmrd file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others.
```

And well I cannot log in. I have tried to via ssh as well. It says can't cd to my home dir. How can i regain root access using this live CD??

---

### Post by SuperSonic4 on 2009-03-01
Does recovery mode on your normal install not work? Press Esc at the grub stage

---

### Post by freakinjonathan on 2009-03-01
oh yeah forgot about that. well now at least I have privilages to mess around with it yay. Lets see how this goes

---

### Post by bodhi.zazen on 2009-03-01
Moved to general help.

See these links :

 (.dmrc) : [http://ubuntuforums.org/showthread.php?t=489171](http://ubuntuforums.org/showthread.php?t=489171)

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Slim Odds on 2009-03-01
> **freakinjonathan said:**
> ok so I completely f'd up the permissions in my ubuntu computer. It wouldn't even load up gnome or anything. I popped in the live CD and chmodded the whole drive as readable and writable by anybody. That was able to start up gnome. Now i get the error

Why in the heck would you do that?

---

### Post by bodhi.zazen on 2009-03-01
> **freakinjonathan said:**
> I popped in the live CD and chmodded the whole drive as readable and writable by anybody.

I missed that in my first response. The only way to recover from this is to re-install.

I suppose you could *try* to go through your system file by file, directory by directory and restore your permissions, but this will obviously take quite some time and you need a working installation to compare to.

You should not change permissions of system files like this. If you need to edit them , use sudo.

---

