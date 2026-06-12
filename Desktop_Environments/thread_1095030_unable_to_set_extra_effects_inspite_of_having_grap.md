---
title: "unable to set extra effects inspite of having graphics card"
date: 2009-03-13
forum: Desktop Environments
---

### Post by abhinav.p on 2009-03-13
my hp laptop has hardy installed in it.has a pre installed graphics card  (nvidia 8400 MGS 256MB card).but i am unable to set the extra effects(change desktop background,visual effects tab).how do i make it recognise it?the very reason i installed it was 4 the extra effects and graphics...

---

### Post by x33a on 2009-03-13
have you loaded the graphics drivers?

see

System -> Administration -> Hardware drivers

---

### Post by abhinav.p on 2009-03-13
i did that it showed that the drivers cannot be installed because nvidia cannot be given in repositories as they are not free software.where can i get them?

---

### Post by x33a on 2009-03-14
open System -> Administration -> Software Sources then enable main, universe, multiverse and restricted repositories.

then click on reload, and check if you can install the driver through hardware drivers.

---

### Post by abhinav.p on 2009-03-14
due to some reason the method u stated did no begin downloading.network problem maybe.googling was not much help either.can anyone tel me or give a site which can guide in a step wise manner?

---

### Post by taurus on 2009-03-14
So your computer is not currently connected to the net?  Personally, I would try to get that going first.  Then, it's much easier to install nvidia from the repos.  

Otherwise, you have to download and install it by hand.

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

---

### Post by abhinav.p on 2009-03-14
no i am connected to net.but it is wireless and i can only set the export commands in the terminal.i even edited the .bashrc file to include the export commands.still for some reason synaptic does not just stat downloading...

---

### Post by taurus on 2009-03-14
What is the exact export command you have to run from a terminal?  Have you looked in Network Manager to set your wireless network from there?

---

### Post by abhinav.p on 2009-03-14
export http_proxy=http://host.com:port/
export http_proxy=http://172.16.1.5:8080/



i have added them in my .bashrc file for connecting to net via terminal.is there anyway i can set it in synaptic?

---

### Post by taurus on 2009-03-14
That's proxy.  Go into System -> Administration -> Synaptic Package Manager -> Network and configure your proxy in there.

---

### Post by abhinav.p on 2009-03-14
hi thanks.i was nt aware we had to set it in network.i thought terminal sets it for the whole system...

---

### Post by abhinav.p on 2009-03-14
hi it is set but still cannot change the resolution.the maximum offered is 640 by 480.it was way less than initial 1024by768.how can i change it?

---

### Post by taurus on 2009-03-14
Have you installed nvidia driver for your graphic card now that you have configured proxy in synaptic?

---

### Post by abhinav.p on 2009-03-14
yes the graphics are working but i cannot set resolution beyond 640by 480.what can i do to restore it?

---

### Post by taurus on 2009-03-14
Have you looked in System -> Preferences -> Screen Resolution?

---

### Post by abhinav.p on 2009-03-14
yeah thats where i am unable to set the resolution beyond the stated value...

---

### Post by taurus on 2009-03-14
Run this command and see if there is nvidia on the list of modules.

```
lsmod
```

---

