---
title: "how to restore root password"
date: 2011-11-05
forum: Desktop Environments
---

### Post by forsubhi on 2011-11-05
I miss my root password and when I go to recovery mode , it prompts me to enter it 

please help me !

---

### Post by bluexrider on 2011-11-05
> **forsubhi said:**
> I miss my root password and when I go to recovery mode , it prompts me to enter it 

please help me !

sudo passwd root
sudo passwd -u root

When you&#8217;re done Log Out

On  the Login Screen, select ***Other,*** then type the &#8216;root&#8217; (without quotes) for the username and the password you created to login.

---

### Post by Rodney9 on 2011-11-05
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Psychocats to the rescue !

---

### Post by forsubhi on 2011-11-06
when I select drop to shell , it requires my root password which I forgot it

---

### Post by lisati on 2011-11-06
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2011-11-06
> **bluexrider said:**
> 
On  the Login Screen, select ***Other,*** then type the ‘root’ (without quotes) for the username and the password you created to login.

This won't work. In Ubuntu, like in most Linux distributions, the root login via the GUI is disabled by default.


@OP

If your user has full admin rights, you can lock/reset the root account password (for instructions, check out the link posted by lisati). If the root account password is locked, you won't be prompted for a password in the recovery mode (or single user mode).

If your user has limited or no admin rights, then you will have to reset the root password: 

Reboot the computer and during the boot process hold down the Shift key. 

When the grub menu appears highlight the recovery mode option. 

Press e for edit and replace the **ro single** kernel parameters at the end of the *linux* line with **rw init=/bin/bash**.

Press Ctrl+x to boot the computer and wait for all boot processes to finish. 

Remount the root partition with read/write privileges:
```
mount -o remount,rw /
```

and reset the root password:
```
passwd root
```

press Ctrl+Alt+Del to reboot.

---

### Post by forsubhi on 2011-11-25
thank you very much sisco311 
your solve is perfect and my thread is solved 
but there is small note 

I didn't find ro single instead I found (( ro recovery nomodeset )) and changed it to (([B]rw init=/bin/bash))


[/B]

---

