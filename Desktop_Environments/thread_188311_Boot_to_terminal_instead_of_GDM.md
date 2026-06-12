---
title: "Boot to terminal instead of GDM?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by bond00 on 2006-06-03
As the title says, I would like Ubuntu to boot to a terminal instead of the GDM login screen. I read it has something to do with changing inittab to run level 2 or 3. I checked my inittab and it the current run level is 2. 

```


# The default runlevel.
id:2:initdefault:



```

Any ideas? Thanks...

---

### Post by skinnygmg on 2006-06-04
read this....

[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/runlevels.htm#_Toc38902028](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/runlevels.htm#_Toc38902028)

---

### Post by bond00 on 2006-06-04
Thanks for the reply, but I think Ubuntu must be different somehow than Redhat and other distros because right now my inittab file has an initdefault of 2 as I stated in my first post. An initdefault of 2 according to the website you posted and most other websites I've found should boot to "terminal multiuser without NFS". Is there another setting somewhere that takes over and loads X11 and GDM automatically after init 2 has completed? Maybe I should do a:

chmod -x /etc/init.d/gdm

Any other ideas? Thanks for the help...

---

### Post by joelito on 2006-06-04
system -> administration -> services
enter your password
Uncheck Graphical Login Manager (GDM and/or KDM)

---

### Post by bond00 on 2006-06-19
for others wondering how to do this:

chmod -x /etc/init.d/gdm

Unchecking the GDM as the previous post suggests, only stops the GDM for that session. After reboot, it goes to GDM again instead of the terminal login.

---

### Post by Ramses de Norre on 2006-06-19
Or install sysv-rc-conf and use that to disable the init script.

---

### Post by Tominator on 2007-03-07
I have the opposite problem I messed up and now when I start up I get a terminal. Took me awhile to find the startx command and would rather get back to the way I was. Thanks, Tom.

---

### Post by tbodine on 2007-03-07
> **bond00 said:**
> for others wondering how to do this:

chmod -x /etc/init.d/gdm

Unchecking the GDM as the previous post suggests, only stops the GDM for that session. After reboot, it goes to GDM again instead of the terminal login.

Actually, I used to boot straight to terminal and just used the unchecking GDM from the services, which worked fine when I rebooted and everything.

---

### Post by ghowriter on 2008-03-07
I too was looking for a way to boot Ubuntu without the Xserver. I am trying to install the NVIDIA drivers for my graphics card and they will NOT install when in the Xserver is running. I registered here to tell you that I have been searching for a way to do this for a year now with NO success. Either the makers of UBUNTU decided to leave this out or hide it so well that there is no way to do it. That is a lot like the way Microsoft does things. I have already solved the issue by removing Ubuntu and installing FC8 and have NOT had any problems since. I have emailed Ubuntu directlty over the last year or so asking for this feature without success - they never respond. I guess that they, also like Microsoft, only support the people who pay for it.

Save yourself the headaches and get a real distro and leave this mimic of Microsoft to the babies who need their computers to do everything for them.

---

