---
title: "Keyboard no longer works in Kubuntu 8.04.2 after latest update."
date: 2009-05-05
forum: General Help
---

### Post by tominglis on 2009-05-05
My keyboard no longer works in Kubuntu 8.04.2 after the latest update.

I think the update included the updated Linux kernel and Nvidia drivers (although there may also have been security updates which install by default).

I can use the keyboard in Grub and to type in my login password, but once the desktop has loaded up the keyboard doesn't work.

I updated the computer while using it, and the problem manifested itself a while later, without a restart, as far as I'm aware. I was using Firefox, Kontact, and Skype at the time.

I tried booting the previous kernel, which had no effect, and also booting as root user and doing startx (which worked). So perhaps one of the updates affected my KDE user account settings in some way?

Any help would be hugely appreciated, as I really need to get back to work!

Many thanks,

Tom

---

### Post by tominglis on 2009-05-05
Does anyone know what could be wrong here?

Is there a KDE or X related file I can delete or edit here to get my keyboard back!?

I would massively appreciate any solutions you might have! :-)

---

### Post by tominglis on 2009-05-05
I have found a solution in this thread, which I will test out shortly and confirm here.

[http://ubuntuforums.org/showthread.php?t=458036](http://ubuntuforums.org/showthread.php?t=458036)

---

### Post by Zorael on 2009-05-06
When I got this, I reconfigured HAL and that solved it.
```
$ sudo dpkg-reconfigure hal
```
But I think I couldn't even enter my login password, whereas yours sound to be a user-specific thing.

If that solution (at that link you posted) doesn't work, try creating a new user and see if it works properly logged in as him/her/it.
```
$ sudo useradd
```
Alternatively, rename the **.kde** dir in your home directory. May have to be done when logged out. You *will* lose all your KDE-specific settings though.
```
$ mv ~/.kde ~/.kde-backup
```

---

### Post by tominglis on 2009-05-08
The slow keys accessibility feature was the problem here! I think that the option for that should definitely be off by default (perhaps it is in KDE4?)

Thanks so much for your prompt and detailed reply!

---

