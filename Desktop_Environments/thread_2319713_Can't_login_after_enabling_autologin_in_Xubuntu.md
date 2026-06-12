---
title: "Can't login after enabling autologin in Xubuntu"
date: 2016-04-06
forum: Desktop Environments
---

### Post by m5rc on 2016-04-06
I changed a Xubuntu 14.04 system to autologin and now it still prompts for a password. If I enter my password, it doesn't work. If I press Enter, it doesn't let me in either.

Is this due to the encrypted filesystem? 

So far I tried to edit /etc/lightdm/lightdm.conf.d/10-xubuntu.conf and add a line that says "autologin=" (to disable the autologin) but it tells me the filesystem is in read-only mode and it can't write changes.

I tried to boot up under the "network" option because I read that this will mount the filesystem in read/write mode, but it seems to just hang there with a flashing underscore (not a command prompt) after doing some filesystem checks that went OK.

Any ideas?

Thanks!

---

### Post by ajgreeny on 2016-04-06
Did you edit the lightdm configuration file from a live system? 
If so did you do it as root, even though it was while running another filesystem from which to carry out the edit?  Try ```
sudo nano /path/to/file
```

I have no experience of encrypted filesystems so am not sure if that is anything to do with this problem, but as you can see that file in your installed system, and it is therefore unencrypted in order to be read, I would think it is not involved.

---

### Post by m5rc on 2016-04-06
Thanks ajgreeny, I did it from grub's recovery mode, with the "root" option. I ran "sudo nano /path/to/file" and when it tried to save it said it didn't have write access. I'm not sure what to do next, maybe try to mount from a live environment and edit from there? I'm not sure if that's possible with encrypted drives.

---

### Post by ajgreeny on 2016-04-07
Recovery mode mounts the filesystem as read-only by default.
Try running the command ```
mount -o rw,remount /
``` to remount it read/write and then see if you can edit the lightdm configuration file this time.

---

### Post by m5rc on 2016-04-07
Thank you--that did the trick.

---

