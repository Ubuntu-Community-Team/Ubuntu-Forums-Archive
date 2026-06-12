---
title: "broken GUI login in ubuntu caused by changed UID"
date: 2012-08-31
forum: Desktop Environments
---

### Post by mattpatey on 2012-08-31
Please can anyone help me? In ubuntu 12.04 (64bit) I changed the UID for a user from 1000 to 1027. (The original reason for this was that I read that having the same UID for the same users on different PCs makes things easier for setting up samba networking, and this was a clean install so it seemed like a good idea at the time!). I changed it using the following:

usermod -u 1027 dave

After this I couldn't log in with the GUI. All the files in /home/dave seemed to be owned by dave:dave, but I ran chmod -Ru /home/dave to see if this fixed things. It didn't. So I decided to change things back to how they were (again using usermod), but I still can't log in.

In /var/log/auth.log I get can see a couple of errors:
... gnome-keyring daemon [9068] couldn't create socket directory: Permission denied
... gnome-keyring daemon [9068] couldn't bind to control socket: /tmp/keyring-pcbweM/control: No such file or directory

In /var/log/syslog I also get some errors on logging in:
... pulseaudio [10390]: [autospawn] core-util.c: Failed to create random directory /tmp/pulse-tXODLWvtrqv: Permission denied
... pulseaudio [10390]: [autospawn] core-util.c: Failed to symlink /var/lib/lightdm/.pulse/b621767c265ec46b75a559f200000003-runtime.tmp: Permission denied
... pulseaudio [10390]: [autospawn] lock-autospawn.c: Cannot access autospawn lock.
... pulseaudio [10390]: [autospawn] main.c: Failed to acquire autospawn lock

If I try to create new users I get the same problem. I can still do GUI logins with another (previously existing) user on the system. Is there some way to fix this without reinstalling?

---

### Post by LewisTM on 2012-08-31
Did you update the ownership on Dave's files?
Running 
```
sudo chown -R 1027:1027 /home/dave
```
should fix things.
Reboot to make sure all temporary files are wiped out.

Cheers!

---

### Post by mattpatey on 2012-08-31
Thanks LewisTM. The files were owned by dave (I have found that usermod automatically updates files in the user's home directory that are already owned by that user).

I found the cause of the problem in the end. The /tmp/ directory was owned by my username with 755 permissions and the sticky bit wasn't set so no other users could write temporary files:

```
chmod 777 /tmp
chmod +t /tmp
sudo chown root:root /tmp
```

Everything works fine now and I have been able to change the UIDs as I originally wanted.

I'm not sure how this got messed up. Maybe when I was running chown -R in users' home directories I forgot the -h switch and a symlink pointed to /tmp, although I can't see any symbolic links pointing here. Anyway, it is working now. Hopefully I haven't broken anything else and not yet realised it!

---

