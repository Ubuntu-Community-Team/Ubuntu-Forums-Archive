---
title: "[SOLVED] Unable to restart the OS"
date: 2008-10-25
forum: Desktop Environments
---

### Post by techie_india on 2008-10-25
Hi all,

Im using Ubunutu 8.04.
Whenever I press the restart button, 
after shutting down everything, 
It just get hangs , it will not restart

I use to shut it manually by pressing the reset button.

Thanks and Regards
Anshuman Srivastava

---

### Post by sethvath on 2008-10-25
Which version of ubuntu is this? 8.04 hardy or 8.10 intrepid rc?

Something is refusing to terminate, that might explain the "hang"

To force a reboot from terminal 

sudo reboot -r

---

### Post by _Narcisse_ on 2008-10-25
Hi, 

I don't know where the problem comes from but my advise is to make a clean reinstall or at least to force a disk check if you rebooted manually several times.

To check the filesystem, type this in a terminal :

```
sudo touch /forcefsck
```

As sethvath said, it may be a process, an application that refuses to terminate. Seems strange to me.

Is the problem recent ? Is that a new install ?

---

### Post by mikjp on 2008-10-26
Google the name of your computer or motherboard  + "ubuntu cannot shutdown". These problems are hardware specific.

---

### Post by techie_india on 2008-11-11
> **sethvath said:**
> Which version of ubuntu is this? 8.04 hardy or 8.10 intrepid rc?

Something is refusing to terminate, that might explain the "hang"

To force a reboot from terminal 

sudo reboot -r

It is 8.04 hardy
It is also a new installation , from the day one it is hanging :(
Ubuntu automatically disk checks 

Thanks and Regards

---

### Post by techie_india on 2008-11-14
> Google the name of your computer or motherboard + "ubuntu cannot shutdown". These problems are hardware specific.

Thanks for suggestion.
I have gooogled with the following keywords :
Intel G31 Express + ubuntu + restart problem

It shows some link ,

The solution is given in the following link :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754)

So now the restarting problem is solved . 
Thanks a lot for the sugggestion
:popcorn:
Regards
Anshuman

---

