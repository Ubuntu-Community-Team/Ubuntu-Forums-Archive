---
title: "I can't use sudo!!"
date: 2006-08-24
forum: Desktop Environments
---

### Post by riaancornelius on 2006-08-24
I've just installed dapper (from the alternative cd), and now I can't use sudo.... 
The only thing I did was to create a user manually before running the 'sudo oem-config-prepare' command.

It seems this was a bad plan. Any way to undo the damage I did?

---

### Post by riaancornelius on 2006-08-24
btw, I also can't see 'Add / remove applications' and most of the stuff in the 'Administration' menu.

---

### Post by Ramses de Norre on 2006-08-24
First we need the output of 'groups', if there is no admin in the list you have to boot into recovery mode and do ```
adduser username admin
``` (replace username by your current username)

If you are in the admin group: Can you boot in recovery mode and do ```
less /etc/sudoers
```
Post the whole contents of the file here.

---

### Post by michux on 2006-08-24
You can always edit the /etc/sudoers file. Puth them something like: ```
%admin ALL=(ALL) ALL
``` and then add your user to the admin group in ```
/etc/group
```. Should help.

Of course these things needs to be done in chroot environment, e.g. by starting a Live-CD and chrooting to your mounted root partition like: ```
chroot /mnt/your_root
```

---

### Post by Ramses de Norre on 2006-08-24
He can't because he can't use sudo.. He'll have to do this in recovery mode but that's not easy if you don't know the commands. That's why I wanted to find the problem first.

---

### Post by michux on 2006-08-24
> **Ramses de Norre said:**
> He can't because he can't use sudo.. He'll have to do this in recovery mode but that's not easy if you don't know the commands. That's why I wanted to find the problem first.

I edited the post to mention it's supposed to be done in chroot. I thought it's obvious :)

---

### Post by Ramses de Norre on 2006-08-24
> **michux said:**
> I thought it's obvious :)
Not for everyone ;)

---

### Post by carontis on 2006-08-24
If you can't use sudo, have you tried to use simply "sudo su? It's the same but sometimes (I don't know why) it gives permissions to enter; other way should be using "su --" but this will ask you exact root password (not the user-root) and from there you should be able fix the error.
This I did long ago and it worked well. Hope for you too.

---

