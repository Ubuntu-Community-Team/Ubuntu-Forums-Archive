---
title: "Ubuntu 9.04 beta: Synaptics not working"
date: 2009-04-05
forum: General Help
---

### Post by BazookaAce on 2009-04-05
Hi, 

I upgraded to 9.04 beta today, and everything is working fine. Well, almost. Synaptics will not start, and it shows me this error:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

What to do? Can i fix this, or shall i just wait for the final release of 9.04? It's not a really big problem, but it would be nice to install new things on my computer.

---

### Post by BazookaAce on 2009-04-06
*BUMP*

Update: The sound doesn't work anymore. But i noticed now that i have 72 new updates and some updated alsa-files are in there. But i can't upgrade because of the error i get (look on the first post).

So can anybody help? I know this is a beta, but if i can't upgrade and update the system, how in hell can it get any better?

---

### Post by Hospadar on 2009-04-06
Much like the error message says:
Open a terminal (Applications-Accessories->Terminal) and run```
sudo dpkg --configure -a
```

After you do that you can update.

If dpkg (the backend of apt-get and thus also synaptic) gets killed or crashes or times out during certain operations, it will throw this error when you try to run it again, and you just need to use that command to clean things up and run again

---

### Post by BazookaAce on 2009-04-06
Thanks, but i get this message back:

```
steffen@steffen-laptop:~$ sudo dpkg --configure -a
[sudo] password for steffen: 
Setting up initramfs-tools (0.92bubuntu27) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28sickboy-kuki
Cannot find /lib/modules/2.6.28sickboy-kuki
update-initramfs: failed for /boot/initrd.img-2.6.28sickboy-kuki
dpkg: subprocess post-installation script returned error exit status 1
steffen@steffen-laptop:~$
```

---

### Post by BazookaAce on 2009-04-06
Oh my freakin' god i did it!

Just navigated to /lib/modules/ and made a folder with the name "2.6.28sickboy-kuki", and then run "sudo dpkg --configure -a
" again, and now it works fine. 

I did also fix the sound problem, so i think my problems are solved!

---

