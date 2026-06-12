---
title: "etc/sudoer is hosed"
date: 2005-07-12
forum: Desktop Environments
---

### Post by Slothrop on 2005-07-12
I am fairly new, but have searched the forums and got only partial answers to my situation: I was trying to edit etc/sudoer in order to get firestarter to load without a password prompt and of course created a syntax error. I have learned that I should have used visudo and will in the future, but now I am sort of stuck. 
     How can I access etc/sudoer without sudo? So far all of my answers have included using sudo, which I cannot do. I know that I can create a root account, but I have very limited command prompt knowledge and usually get lost after a few minutes, with no internet access. 
  All I need to do is edit etc/sudoer and remove the line I added, and yes I know I should have beacked it up, which I have backed up all of my other edited scripts, I just didn't think this edit was going to be complicated--big mistake.

---

### Post by Xian on 2005-07-12
Read this [THREAD](http://ubuntuforums.org/showthread.php?t=14366) for more information.

---

### Post by az on 2005-07-12
Just boot into recovery mode instead of all the init=/bin/bash crap.  That is what recovery mode is for...

---

### Post by Xian on 2005-07-12
[QUOTE=azz]Just boot into recovery mode instead of all the init=/bin/bash crap.  That is what recovery mode is for...[/QUOTE]
Heh. You did mention that in the linked thread...but it was a nice touch. :)

---

### Post by az on 2005-07-13
[QUOTE=Xian]Heh. You did mention that in the linked thread...but it was a nice touch. :)[/QUOTE]

...So I did.  I had not seen that....


Maybe it would be simpler to just delete the suders file from within the recovery mode and do

apt-get install --reinstall sudo

(you are root in the recovery console...  You do not need to start the command with sudo as usual.)


I am not sure that the sudoers file is created with the user's profile by the sudo package or some ubuntu-desktop dependancy...

I should give that a try when I have a chance...

---

