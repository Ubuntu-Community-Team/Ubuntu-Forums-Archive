---
title: "[SOLVED] Need Help! Sudo Error"
date: 2008-12-31
forum: General Help
---

### Post by ash369 on 2008-12-31
Hey all I'm new with ubuntu so go easy :P

I recently installed ubuntu and at first i was a bit confused as to how to connect to the internet but i figured that out and everything was running great. Anyway the problem now is i changed the sudoers file to make it stop asking me for a password every 5 seconds, and after i saved it i can't run any sudo commands or run any admin tools.

ashley@ashley-desktop:~$ sudo
>>> sudoers file: syntax error, line 25 <<<
sudo: parse error in /etc/sudoers near line 25
ashley@ashley-desktop:~$

Please help!

---

### Post by SonnHalter on 2008-12-31
you have to open the file back up and look for ANY error that could have been made (typo,logic,ect) 

like it said, look in line 25 of that document

---

### Post by drs305 on 2008-12-31
check to see if you are still in the admin group:
```
id
```
You should see your username and *(admin)* in the groups.

If not, and you can't use sudo, boot to the recovery mode and select the option "boot to the root prompt" and see if it will allow you to enter the root shell. If you can get to the command line:
```

adduser *your.user.name* admin 
reboot now

```
Example: adduser john admin

If you still can't use sudo after the reboot, the sudoers file may need editing. Return to the recovery mode and see if you can find the error with:
```

cp /etc/sudoers /etc/sudoers.bak && cp /etc/group /etc/group.bak
sudo visudo

```

---

### Post by ash369 on 2008-12-31
I opened the file using gedit /etc/sudoers and i can see what i need to delete, i just can't save it after i've deleted it.

---

### Post by hyperdude111 on 2008-12-31
This is a guess but i would enable the root account the remove all traves of sudo from synaptic. Once you have done that try to re-install hopefully this will override the system file.

---

### Post by ash369 on 2008-12-31
ashley@ashley-desktop:~$ id
uid=1000(ashley) gid=1000(ashley) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),114(netdev),124(sambashare),1000(ashley)
ashley@ashley-desktop:~$ 

I have no idea what that means...but where do i go from here?

---

### Post by damis648 on 2008-12-31
Try this in single user mode (recovery mode, drop to a root shell): (just a guess mind you)
```
dpkg-reconfigure sudo
reboot
```
I am not on Ubuntu right now so I cannot tell you much more at this point.

---

### Post by drs305 on 2008-12-31
> **ash369 said:**
> ashley@ashley-desktop:~$ id
uid=1000(ashley) gid=1000(ashley) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),114(netdev),124(sambashare),1000(ashley)
ashley@ashley-desktop:~$ 

I have no idea what that means...but where do i go from here?

Your name isn't listed in (admin), so you have to add it back in the recovery mode. Reboot.

When you get to the grub menu, select the recovery mode option. When the next menu appears, select "boot to the root prompt". Enter your password.

At the command line prompt, type:
```

adduser ashley admin
reboot

```

That should add you back into the admin group and probably restore your 'sudo' capability.

---

### Post by ash369 on 2008-12-31
adduser your.user.name admin 
reboot now

Did this and now i can use admin tools, just now i still can't use sudo commands. I tried using:
cp /etc/sudoers /etc/sudoers.bak && cp /etc/group /etc/group.bak
sudo visudo

But got the error cp:missing destination file after '/etc/group.bak

These is a line in my sudoers file which needs to be deleted, i know this its just how to do it thats the problem because sudo visudo doesn't work.

---

### Post by ash369 on 2008-12-31
dpkg-reconfigure sudo
reboot

Tried the above code as root and still no luck running sudo commands, i guess i need to make a new sudoers file with a different name and then rename the old one to sudoers.bak and then rename the new one to sudoers?

Or something along those lines would work i think, anyone know how i would go about doing this?

Thanks.

---

### Post by ash369 on 2008-12-31
Hey all, thanks for your help.

I must not of seen it correctly but i pressed ctrl+V and scrolled to the bottom of the page and deleted what is was that was causing the problem. Also changed the menu.lst to boot defult 7 which is my XP partition.

Thanks again! ^^

---

### Post by drs305 on 2008-12-31
Here is a standard sudoers file:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Try to replace your sudoers file with this one. Make a copy of this file and place it in your home directory (since you don't have sudo privileges). Name it sudoers1.

I'm assuming you can't get to your sudoers file without being able to use sudo, so boot into recovery mode to the root prompt and run the following:
```

mv /etc/sudoers /etc/sudoers.123108
cp /home/ashley/sudoers1 /etc/sudoers
chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
reboot

```

---

