---
title: "System policy prevents me from changing configuration"
date: 2009-02-28
forum: General Help
---

### Post by beejer on 2009-02-28
Hi guys-

I have just picked up our Church's PC which is a Dell with Ubuntu 8.04 installed on it. 

There are few things which I need to set up and I am completely puzzled by the fact that the installation doesn't allow me to change any(!) system configuration. 

For example I simply wish to install a few more Ubuntu packages through Add/Remove software, I'll enter the admin password and it always fails. I use the terminal enter the sudo and it still fails. 

Another example: I can't unlock any of the > system > admin functions as well. At least here I got the message that system policy seems to stops me, but there are no other users set up on this system apart from root.

Any chance of help? I am to the point to just wipe out the system and reinstall it afresh. :confused:

Thx

---

### Post by dbbolton on 2009-02-28
> **beejer said:**
> Hi guys-

I have just picked up our Church's PC which is a Dell with Ubuntu 8.04 installed on it. 

There are few things which I need to set up and I am completely puzzled by the fact that the installation doesn't allow me to change any(!) system configuration. 

For example I simply wish to install a few more Ubuntu packages through Add/Remove software, I'll enter the admin password and it always fails. I use the terminal enter the sudo and it still fails. 

Another example: I can't unlock any of the > system > admin functions as well. At least here I got the message that system policy seems to stops me, but there are no other users set up on this system apart from root.

Any chance of help? I am to the point to just wipe out the system and reinstall it afresh. :confused:

Thx
If the root password has not been set, boot into "recovery mode" from GRUB (If there is a root password, see below. By default there is no root password in Ubuntu.). It will bring you to a command line. Enter this command to set a root password (for future use):
```
passwd root
```Next you need to add yourself to the sudoers file. Enter this command:
```
visudo
```Look for the line like:
```
[FONT=monospace]
[/FONT]root    ALL=(ALL) ALL

```and add an identical line below it but replacing root with your username. Here is some more info on using the visudo command: [http://www.sudo.ws/sudo/man/visudo.html](http://www.sudo.ws/sudo/man/visudo.html)

If the root password has been lost, just google "lost root password" and you will find some tutorials explaining how to reset it. I recommend using the live CD method.

---

### Post by beejer on 2009-03-14
wokred like a treat!
thx

---

### Post by dbbolton on 2009-03-14
No problem :)

---

