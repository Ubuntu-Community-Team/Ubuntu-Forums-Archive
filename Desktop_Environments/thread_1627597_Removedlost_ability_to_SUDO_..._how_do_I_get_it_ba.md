---
title: "Removed/lost ability to SUDO ... how do I get it back?"
date: 2010-11-21
forum: Desktop Environments
---

### Post by WinRiddance on 2010-11-21
Not realizing that sudo is located in /usr I went ahead and assigned myself privileges to my /usr folder via sudo chown -R

... which promptly resulted in me not being able to use sudo via the terminal anymore. I tried going to the login screen recovery console in order to restore sudo but can't seem to get it done. The only helpful thing that I could find in the forum was for this command:

> chown root:root /usr/bin/sudoThere's a second line to add but I can't get past the first command since I receive this error/message:

> sudo: must be setuid rootSince Ubuntu is the only OS on my system, I do not get a dual boot screen with several options like last kernel, recovery mode, etc. My screen goes directly to the Ubuntu 10.10 login screen. I have the option of getting into the recovery console, but that just gives me the same "must be setuid" message as above.

---

### Post by wther on 2010-11-21
You might want to reassign a new root password from Grub. That will definitely solve your permission problems :).   I've googled "grub root password forget" and tons of good results.

---

### Post by garvinrick4 on 2010-11-21
Just for the heck of it what does your:
```
gksudo gedit /etc/sudoers
```
look like

---

### Post by WinRiddance on 2010-11-21
Thanks, but this is not a password issue and I have no problem logging into my session. This strictly has to do with the fact that I lost my "sudo" ability in the terminal as a result of changing file/permission ownership of a location, known as ... /usr

If possible, I'd like for someone to tell me step by step, with included commands, what I need to do in order to get my sudo privileges restored to me again. I'm the only user/admin of this machine and need full sudo access.

---

### Post by WinRiddance on 2010-11-21
> **garvinrick4 said:**
> Just for the heck of it what does your:
```
gksudo gedit /etc/sudoers
```look like


Thanks a bunch. Opened the terminal and tried that, causing another program or command to open ... starting administrative application ...
However, a few seconds later that vanished and I was back at the original screen with my ...
winriddance@winriddance-laptop:~$

Oh, darn, I just remembered that it wasn't just the /usr folder which I assigned with privileges to myself **but also the /etc folder** as well. I did both of them at the same time with a single chown command ...

---

### Post by wei2912 on 2010-11-21
There's a hidden file called .sudo_as_admin_successful in everyone's account's home folder that can be shown with ctrl-h. It might help.

---

### Post by northern lights on 2010-11-21
> **WinRiddance said:**
> Thanks, but this is not a password issue and I have no problem logging into my session. This strictly has to do with the fact that I lost my "sudo" ability [...]

If your observations of having "lost the sudo ability" are correct,

> **garvinrick4 said:**
> Just for the heck of it what does your:
```
gksudo gedit /etc/sudoers
```
look like

this is exactly what you want to be looking at.

Did you change your username or are you logging in from a user account other than the one you created in the installation process?
That would explain things a bit.
What error response do you get when attempting to run any process as root?

[/etc/sudoers - Ubuntu Community Documentation]("https://help.ubuntu.com/community/Sudoers")

---

### Post by jocko on 2010-11-22
Changing the permissions on anything outside your home directory is a very bad idea if you don't know exactly what you're doing (and if you know what you're doing you would have no urge to change the permissions of the /usr directory...).

Boot into recovery mode and drop to a root terminal, then restore the correct permissions on *all* the files you changed...

But, since you ran chown on all files and folders in /usr and /etc, I'm sure it would take several weeks to find the proper permissions for every single file, so a complete reinstall is probably your safest option...

---

### Post by WinRiddance on 2010-11-22
**Thanks everyone!**

I've been experiencing so many problems with Ubuntu 10.10 that I went ahead and reverted back to 10.04 with a clean install yesterday. Now everything is fine again. I'll mark this thread as solved.

---

