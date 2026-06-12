---
title: "Deleted /tmp using rm -R /tmp now GDM keeps on crashin"
date: 2008-06-19
forum: Desktop Environments
---

### Post by nair.arun on 2008-06-19
](*,) #-o I accidentally deleted the /tmp directory using sudo rm -R /tmp everything was fine till the time I didn't restart.  Now after restart I'm not able to login through the GDM and tty 1-6 is just blank with cursor blinking.  :( I'm due for a submission of my work and I want to complete it and recover from this problem.

Please Help Me.

---

### Post by joselin on 2008-06-19
Use a live cd, mount your root partition and then create the directory tmp on your mounted root partition.

---

### Post by nair.arun on 2008-06-19
> **joselin said:**
> Use a live cd, mount your root partition and then create the directory tmp on your mounted root partition.

Just tried it doesn't works GDM keep on crashing stating "The greeter application appears to be crashing. Attempting to use a different one"

---

### Post by krlhc8 on 2008-06-19
/tmp isn't really that important of a folder since random downloaded stuff is stored there, that's all.  Are you sure you didn't delete anything else?  

Anyways, reboot your machine, hit Escape to get to the GRUB menu, select the recovery-mode option, which should boot you up to a terminal.  Just recreate the directory with the command below, and you should be good to go:  

```
sudo mkdir /tmp
```


In your root directory, you should see the following directories: 

bin, boot, dev, etc, home, initrd, lib, lost+found, media, mnt, opt, proc, root, sbin, srv, sys, tmp, usr, var

---

### Post by nair.arun on 2008-06-19
> **krlhc8 said:**
> /tmp isn't really that important of a folder since random downloaded stuff is stored there, that's all.  Are you sure you didn't delete anything else?  

Anyways, reboot your machine, hit F1 to get to the GRUB menu, select the recovery-mode option, which should boot you up to a terminal.  Just recreate the directory with the command below, and you should be good to go:  

```
sudo mkdir /tmp
```


In your root directory, you should see the following directories: 

bin, boot, dev, etc, home, initrd, lib, lost+found, media, mnt, opt, proc, root, sbin, srv, sys, tmp, usr, var

Tried it made the /tmp directory but still doesn't works it just keeps on giving me the error of GDM greeter application crashing attempting to use another one and also my tty 0-6 are blank with the cursor blinking in normal mode but i can access the recovery mode but still doesn't works.  I even tried [http://liltux.wordpress.com/2007/09/05/how-to-fix-the-error-the-greeter-application-appears-to-be-crashing-in-ubuntu/](http://liltux.wordpress.com/2007/09/05/how-to-fix-the-error-the-greeter-application-appears-to-be-crashing-in-ubuntu/) this post to fix the gdm greeter but its already there.

---

### Post by krlhc8 on 2008-06-19
Whenever I had that problem, I would hit ctrl+alt backspace whenever the GDM error message popped up.  Did you load any new kernel recently?  Maybe that's what is causing your problem.  Try loading an earlier kernel in the GRUB menu.  Like 2.6.24-17 or -16 or whatever works.

---

### Post by bijeeshvs on 2008-06-19
hello arun what does gdm says when it get crashed????????????????

---

### Post by nair.arun on 2008-06-19
> **krlhc8 said:**
> Whenever I had that problem, I would hit ctrl+alt backspace whenever the GDM error message popped up.  Did you load any new kernel recently?  Maybe that's what is causing your problem.  Try loading an earlier kernel in the GRUB menu.  Like 2.6.24-17 or -16 or whatever works.

No new kernel has been updated and the older one than this also gives the same error

---

### Post by krlhc8 on 2008-06-19
Did you try pressing ctrl+alt backspace whenever the error popped up?

---

### Post by krlhc8 on 2008-06-19
As a temporary fix, what I did whenever I came across this problem was to edit gdm.conf in the terminal:

```
sudo pico /etc/gdm/gdm.conf
```

Edit the line:
```
Greeter=/usr/lib/gdm/gdmgreeter
```
to say:
```
Greeter=/usr/lib/gdm/gdmlogin
```

It should let you use your computer, but you'll have an ugly login screen.

---

### Post by nair.arun on 2008-06-19
> **bijeeshvs said:**
> hello arun what does gdm says when it get crashed????????????????

It doesn't says anything but just gives a dialog box stating “The greeter application appears to be crashing trying to use a new one...” something like that and then it says that it has crashed 6 times in the last 90 seconds and will wait for 2 minutes before starting again

---

### Post by nair.arun on 2008-06-19
> **krlhc8 said:**
> As a temporary fix, what I did whenever I came across this problem was to edit gdm.conf in the terminal:

```
sudo pico /etc/gdm/gdm.conf
```

Edit the line:
```
Greeter=/usr/lib/gdm/gdmgreeter
```
to say:
```
Greeter=/usr/lib/gdm/gdmlogin
```

It should let you use your computer, but you'll have an ugly login screen.

Tried it but doesn't works I edited it from the live cd and then rebooted to get back in but got the same message

---

### Post by nair.arun on 2008-06-20
> **nair.arun said:**
> Tried it but doesn't works I edited it from the live cd and then rebooted to get back in but got the same message

Any help with this it would be greatly appreciated I'm nearing my project deadline

---

### Post by decoherence on 2008-06-20
The /tmp directory should be world writable and sticky.

```
chmod 1777 /tmp
```

---

