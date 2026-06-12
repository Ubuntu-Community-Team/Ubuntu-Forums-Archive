---
title: "Move and replace files"
date: 2009-01-17
forum: General Help
---

### Post by InsaneNutter on 2009-01-17
Hi, Im guessing this is a simple question but here goes!

I have a folder in root called ut2004 and a folder called patch also in the root folder.

Using the terminal (connected via putty) how can I move all the files and folders inside the patch folder to the ut2004 folder replaceing any files/folders that exist in the ut2004 folder?

Thanks :)

---

### Post by adult swim on 2009-01-17
```
sudo mv -f /path/to/folder/* /ut2004
```

---

### Post by unutbu on 2009-01-17
If the /patch directory has subdirectories, then you could use rsync:
```

sudo rsync -a /patch/ /ut2004/    # Copies contents of /patch into /ut2004
sudo rm -rf /patch  # Be careful -- this deletes /patch

```
Note that when using the rsync command, you need to type the last forward-slash in "/patch/". This tells rsync to copy the contents of /patch/ to /ut2004. Without the forward-slash, the contents get copied to /ut2004/patch/.

---

### Post by InsaneNutter on 2009-01-17
Thanks for the quick replies, I have tried both ways mentioned and get errors as I’ve copied and pasted below.

Could anyone advise what could be wrong?

Thanks.


```

root@localhost:~# sudo rsync -a /patch/ /ut2004/
sudo: /etc/sudoers is owned by uid 500, should be 0

```

```

root@localhost:~# sudo mv -f /root/patch/* /root/ut2004/
sudo: /etc/sudoers is owned by uid 500, should be 0

```

```

root@localhost:~# mv -f /root/patch/* /root/ut2004/
mv: cannot move `/root/patch/Animations' to a subdirectory of itself, `/root/ut2004/Animations'
mv: cannot move `/root/patch/Help' to a subdirectory of itself, `/root/ut2004/Help'
mv: cannot move `/root/patch/Speech' to a subdirectory of itself, `/root/ut2004/Speech'
mv: cannot move `/root/patch/System' to a subdirectory of itself, `/root/ut2004/System'
mv: cannot move `/root/patch/Textures' to a subdirectory of itself, `/root/ut2004/Textures'
mv: cannot move `/root/patch/Web' to a subdirectory of itself, `/root/ut2004/Web'

```

---

### Post by unutbu on 2009-01-17
[list]
[*]You do not need to be logged in as root. For your own sake, please reconsider working too often as root. Instead, work as a normal user as often as possible.  Doing so will reduce the chances of breaking your system. 
[*]/etc/sudoers is owned by the wrong user.
[/list]

To fix the second problem: Reboot. Get to the GRUB menu. You might have to press ESC. Boot into "Recovery Mode". Depending on which version of Ubuntu you are running, you will either be dropped to a root shell or be presented with a menu. If you see a menu, select "drop to root shell".  Now type
```

chown root:root /etc/sudoers
chmod 440  /etc/sudoers
init 2                            # This will get you to the GDM login screen

```

Then try thes "sudo rsync" command:
```

sudo rsync -a /root/patch/ /root/ut2004/
```

---

