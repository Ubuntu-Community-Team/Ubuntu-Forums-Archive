---
title: "password help"
date: 2005-09-09
forum: Desktop Environments
---

### Post by b0s0x79 on 2005-09-09
Ok I think I really screwed myself here.  I cannot log into ubuntu as a user or root, need to know if there is a way to reset password without loggin in.  I tried to change my root password and user password and I think I used the wrong command, when i was reading ubuntuguide i looked at the wrong line and i typed in passwd -l root and then it didn't do anything so i did the same thing as except passwd -l <username>

Any help would be apprecaited.

---

### Post by KingBahamut on 2005-09-09
I think you might be hurtin. 

But, I could be wrong.

---

### Post by macgyver2 on 2005-09-09
[QUOTE=b0s0x79]Ok I think I really screwed myself here. I cannot log into ubuntu as a user or root, need to know if there is a way to reset password without loggin in. I tried to change my root password and user password and I think I used the wrong command, when i was reading ubuntuguide i looked at the wrong line and i typed in passwd -l root and then it didn't do anything so i did the same thing as except passwd -l <username>

Any help would be apprecaited.[/QUOTE]
Okay...the only way I can think of to fix this is to do the following...

Boot with a LiveCD...once you're in, mount your / partition.

Now you're going to go into the shadow file from your real (not live) system.  Use whatever editor you want to open /mnt/etc/shadow (with superuser privileges).  In the second field of the line that begins with your username (and no others!) remove the exclamation mark that is the first character of that field (and no others!).  That should unlock your user account.  Save the file, exit it, and unmount that partition.  Reboot without the LiveCD and try to log in with your username.

Let us know if you have any further questions or issues.

---

### Post by b0s0x79 on 2005-09-09
Ok i got it fixed.  This is what I did, its a neat trick.  When the boot menu came up I type "e" to edit then I scrolled down to the kernel line and hit "e" to edit that line.  at the end of this line I hit spacebar then typed single then enter then i hit "b" to boot from this.  once it booted I could change my password at the prompt by using the "passwd <username>" cammand.  Now all is well.  Thanks for the support guys.

---

### Post by macgyver2 on 2005-09-09
Nicely done.  And a whole lot easier than what I said.  I'll have to remember that.

---

