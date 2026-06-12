---
title: "Root owns my home"
date: 2009-12-17
forum: Desktop Environments
---

### Post by ST3ALTHPSYCH0 on 2009-12-17
Well, I attempted to move my home folder to another partition (just the folder, not a full /home partition). I didn't think and used sudo to create the directory that I move my home folder to and not root owns my home folder.
I tried making myself the owner again:
```

chown -R user.user /media/sdb1/home
chown: changing ownership of `/media/sdb1/home/.gvfs : function not implemented
sudo chown -R user.user /media/sdb1/home
chown: cannot access `/media/sdb1/home/.gvfs : Permission denied
[code]

So then I tried dropping to a root prompt and trying again:
[code]
sudo -s
chown -R user.user /media/sdb1/home
chown: cannot access `/media/sdb1/home/.gvfs : Permission denied

```

This isn't a huge deal for me due to the fact that I'll be reinstalling to new HDDs this weekend (I will migrate my home folder from my primary install to a separate /home partition in the process), but I would like to learn to fix this. I was going to have 3 different versions of Ubuntu installed and have the home folder like this in a home partition: /user (our Karmic install), /jaunty/user, and /lucid/user. I think that I'll just make the username of my other installs jauntyuser and luciduser so that they generate separate home folders from the word "go".

---

### Post by aysiu on 2009-12-17
It probably worked. *.gvs* is always a bit troublesome with the *chown* command.

On a random note, for future reference, you should use ```
sudo -i
``` and not *sudo -s* to get a persistent root prompt.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
It still lists root as the owner... what else can I try. BTW, what's the difference between the -s and -i modifiers? -s was the first one I found.

---

### Post by aysiu on 2009-12-17
```
sudo -i
``` gives you root privileges but uses the root environment.

```
sudo -s
``` gives you root privileges but uses the user environment, so there is a danger in accidentally changing ownership of a user-owned file to root.

---

### Post by ST3ALTHPSYCH0 on 2009-12-18
Oh, I see. Thanks for the info.
Is there any other way to switch folder ownership if that didn't work?

---

### Post by JBAlaska on 2009-12-18
You can always do it the GUI way. Start up a powerful file manager like krusader in root mode, right click on your /home dir, goto properties and change group=root and user=root to group=user user=user (where user is your user name ..duh..). all done.

---

### Post by ST3ALTHPSYCH0 on 2009-12-18
I might give that a try. Nautilus wouldn't let me do it (yes, I was running a root file browser).

---

### Post by CharlesA on 2009-12-18
Strange. Try sudo -i and then run chown -R user:user /media/sdb1/home/(user)

Root should own the /home folder.

---

### Post by sisco311 on 2009-12-18
> **ST3ALTHPSYCH0 said:**
> I might give that a try. Nautilus wouldn't let me do it (yes, I was running a root file browser).

Reboot in *Recovery Mode* and run:
```
chown user\: /home/user/.gvfs
chmod 0700 /home/user/.gvfs
```

~/.gvfs is the mount point for virtual filesystems, you can not change the permissions/owner while something is mounted in the directory.

---

### Post by ST3ALTHPSYCH0 on 2009-12-18
Ah, that makes sense. I assume that I need to substitute my current path for my home directory?

---

### Post by sisco311 on 2009-12-18
> **ST3ALTHPSYCH0 said:**
> Ah, that makes sense. I assume that I need to substitute my current path for my home directory?

Yes.

---

### Post by EoRaptor013 on 2010-06-14
> **JBAlaska said:**
> You can always do it the GUI way. Start up a powerful file manager like krusader in root mode, right click on your /home dir, goto properties and change group=root and user=root to group=user user=user (where user is your user name ..duh..). all done.
Wish it were so easy. Using nautilus (which is pretty "powerful"), when I click on the dropdown lists to change owner and group, the values revert to root and plugdev when I exit the field. You simply can't change the owner/group in nautilus, thunar, or bsc (yes, I started them with gksu).

Arrgh!

---

