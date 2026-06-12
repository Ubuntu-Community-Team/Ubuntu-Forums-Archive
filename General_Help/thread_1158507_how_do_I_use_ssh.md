---
title: "how do I use ssh"
date: 2009-05-13
forum: General Help
---

### Post by flyingsliverfin on 2009-05-13
how do I use ssh?
I do not know the name of the computer, but I know it is windows. can I shh?
And my work desktop is always on, and I know the password, I know the name, but I still don't know how to use it!

---

### Post by whoop on 2009-05-13
You can ssh to a windows machine but you need to install a ssh server for windows on the machine.

---

### Post by flyingsliverfin on 2009-05-13
hm...

---

### Post by Chad.S on 2009-05-13
You can use winexe to get into the Windows box from a Linux box. You can get winexe from ...

[http://eol.ovh.org/winexe/](http://eol.ovh.org/winexe/)

---

### Post by flyingsliverfin on 2009-05-14
okay,
but if I just want to use ssh how do i do it? (to a linux machine)

---

### Post by mbsullivan on 2009-05-14
> okay,
but if I just want to use ssh how do i do it? (to a linux machine)

Assuming that the computer you are going to is running an SSH server and you have a user account on that machine, you can SSH in with the following command:

```
ssh [account]@[ip address]
```

Then provide the password for your user account on the remote machine.

The above command also assumes that the SSH server is running with the default port (which is probably a safe assumption), and that it doesn't use strict security measures.

Mike

PS: As previous people have suggested, you can SSH into either a Windows or *nix box with the same command. The only real difference is that it's typically a lot easier and more common to run an SSH server on a Linux box.

PPS: If you want to look into setting up an SSH server on your machine, see [here]("https://help.ubuntu.com/community/SSHHowto").

---

### Post by Paul41 on 2009-05-14
from the terminal

```
ssh user@ip_address
```

---

### Post by drs305 on 2009-05-14
Here is the ubuntu documentation on SSH. There is a section on Windows as well:
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by Spinitch on 2009-05-14
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] **after installing Jaunty ERROR city** 
im not so new to ubuntu but still a newbie and could really use the help,after i installed the new Jaunty 9.04 i rebooted after an update and now all iget when i boot right after the boot/grub/menu.lst are error messages repeating about 200 tries saying my root/dev failed or no such file or directory and leaves me in busy box after it gives up waiting for root device...ive tried every sudo trick i know (which isnt very much) and all the forum help i could find and im going to pull my brain out through my nose in a min as nothing has worked for me even trying from the live cd, if anyone is having this problem or a solution i would be forever in your dept im a photographer and all my work is on there and my newbie mistake was forgetting to back up my files :sad:( yes i know i know bad SPIN i will try to list the errors ive been getting hopefully will make it easier to help with my issue thank you everyone 


ata3.00: status: DRDY ERR
ata3.00 error: UNC
end_request:I/O error,dev,sdb,sector131
EXT3-fs:cant read group descriptor 7

mount:mounting /dev/disk/by-uuid/9f5cd2cd-413a-4ab0-95a-6408a0c80820 on /root failed:invalid argument

mount:mounting/dev on /root/dev failed: no such file or directory

mount:mounting/sys on /root/sys failed: no such file or directory

mount:mounting/proc on /root/proc failed: no such file or directory

Target filesystem doesnt have /sbin/init. no init found.try bypassing init=_bootarg.

---

### Post by dcottingham on 2009-05-14
I think what you're saying is you want to sit at the Windows machine and ssh into the Linux machine.  My knowledge of Windows is somewhat dated, but last I checked Windows does not come with a ssh client.  A popular ssh client for Windows is putty (Google it).

As someone noted above, you also need to enable the ssh server on the Linux machine -- default ubuntu installation leaves it turned off -- so also follow the instruction in an earlier reply to make sure it's turned on.

---

### Post by alphacrucis2 on 2009-05-14
I quite like the gui ssh client called putty which is available in both windows and linux. Either way the destination machine you connect to, has to be running an ssh server. The openssh-server package is in the ubuntu repos. For windows try google ssh server for windows

---

### Post by flyingsliverfin on 2009-05-16
I think I get it now. Thx every1

---

