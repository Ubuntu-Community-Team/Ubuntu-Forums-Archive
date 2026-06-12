---
title: "Am I Screwed?"
date: 2006-01-03
forum: General Help
---

### Post by TheSource on 2006-01-03
I deleted my hosts file. Well that broke sudo so I dont have access. Also root isn't activated. I went to replace the hosts file in "rescue mode" with

nano /etc/hosts

and I get the following error...

error opening terminal:bterm.

Can anyone help me out? This s!*t is confusing sometimes.

Thanks.

---

### Post by jpkotta on 2006-01-03
You don't need a text editor to manipulate text files.  Sounds like you can run shell commands, so you are not screwed.

```
echo "string" >> /etc/hosts
``` will append "string" (without the quotes) to the /etc/hosts file.  This should be sufficient to get sudo back:
```
echo "127.0.0.1 localhost.localdomain localhost" >> /etc/hosts
```

You can give root a password with ```
sudo passwd root
``` Some people will say that's a bad idea, but I say it fixes situations where sudo fails.

---

### Post by TheSource on 2006-01-04
Well I did that. The hosts file reads....

127.0.0.1 localhost.localdomain localhost

It still doesn't work.

---

### Post by codejunkie on 2006-01-04
reboot the computer at the grub prompt choose recovery mode this will temporarly enable the root account. now set the root password with
```
passwd root
```
reboot the computer by typing reboot and login like normal, open a terminal type 
```
su
``` to gain root access and run
```
export EDITOR=gedit && visudo
```
add your user name to the bottom of the file like this 
```
yourusername ALL=(ALL) ALL
```
save the file and exit now test it by trying an app that requires sudo.

---

### Post by TheSource on 2006-01-04
ok got the root account enabled.

---

### Post by TheSource on 2006-01-04
and i got my hosts file fixed i guess cause i can now use sudo. thanks

---

