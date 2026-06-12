---
title: "Root Password?"
date: 2005-07-29
forum: Desktop Environments
---

### Post by mjsb on 2005-07-29
Hello, I am a new Ubuntu user (I do have some experience with UNIX/Linux though).  And I do not know what the root password is because it never asked me to make one, I have a screenshot...

[IMG]http://www.gfyinc.cc/ubuntu[/IMG]

Thanks In Advance :)

---

### Post by johanvdw on 2005-07-29
Just run "sudo passwd". If sudo asks for a passwd it is the password of the user (like always for sudo). 
You can now set the passwd for the root user and afterward "su" to root.

At least, this worked for me (I used Kubuntu)

---

### Post by mjsb on 2005-07-29
[QUOTE=johanvdw]Just run "sudo passwd". If sudo asks for a passwd it is the password of the user (like always for sudo). 
You can now set the passwd for the root user and afterward "su" to root.

At least, this worked for me (I used Kubuntu)[/QUOTE]
 It will not let me run 'sudo passwd' it says my name is not in the sudoers file

Thanks

---

### Post by Juergen on 2005-07-29
> I do have some experience with UNIX/Linux thoughthat's one of your problems ;-)

Ubuntu's philosophy is to have the root-account disabled and do all administration via sudo. You can set the password, but it is not necessary.
Read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

So your main problem is that you aren't a sudoer. 
Only the first user is added to the sudoers automatically. If mike ist your first or only user, you've run into a bug of Ubuntu's setup.

You can boot into single-user ('recovery mode' in grub) and edit /etc/sudoers via
```
export EDITOR=nano; visudo
```using your favourite textmode editor.

---

### Post by bored2k on 2005-07-29
[QUOTE=johanvdw]Just run "sudo passwd". If sudo asks for a passwd it is the password of the user (like always for sudo). 
You can now set the passwd for the root user and afterward "su" to root.

At least, this worked for me (I used Kubuntu)[/QUOTE]
 That's not the correct way to do things. Ubuntu uses sudo, read up on  [http://wiki.ubuntulinux.org/RootSudo](http://wiki.ubuntulinux.org/RootSudo) .

---

### Post by moldboy on 2005-07-29
I installeed the advanced way, and it asked for root password, but now under my normal account the sudo command doesn't work, and if I were to try and run a program such as Synaptic (I hope i got that right) it askes for password, yeah okay, I use my user password, or the root password, and get an error it is a diffrent error each time but it won't let me run anything that is in the adminstrative panel, perhapse if ubuntu isn't suposeto have a root account then it shouldn't require a password to do things a root user would normaly do.

---

