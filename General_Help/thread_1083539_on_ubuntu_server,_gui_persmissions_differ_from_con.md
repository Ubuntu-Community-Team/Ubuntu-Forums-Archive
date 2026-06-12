---
title: "on ubuntu server, gui persmissions differ from console permissions"
date: 2009-03-01
forum: General Help
---

### Post by sloggerkhan on 2009-03-01
So I installed ubuntu server, so far so good.
Everything's fine from command line.
I have a drive that I want users to have general read/write/create/execute access to. Let's call it a hard drive mounted to /media/public.
I do:
```

sudo chown root:users /media/public
sudo chmod 775 /media/public

```

Now members of the group users can read, write, create directories, etc., in the public drive/directory. 

However, for some reason when I startx for lxde or xfce I no longer have write/create directory access in /media/pubic. The properties dialog for both DEs says I do, but in practice I can't create/move files to the public location despite being able to do so from command line. 

Any ideas why? Is the gui running with non-user permissions, or is there some other reason?

---

### Post by Xiong Chiamiov on 2009-03-01
Can you write in the directory from the CLI as a normal user?  Have you tried using the umask option when mounting it?

---

### Post by sloggerkhan on 2009-03-01
yes, I can write, read, etc, from command line in VT1-6. Just not from the gui. Interesting thing is that properties dialog in gui shows correct permissions, just doesn't apply them. Also, command line sessions spawned from the GUI have the same problem. Is it possible that the GUI runs with a Umask that causes it to ignore group permissions?

---

### Post by sloggerkhan on 2009-03-01
apologize for the double post, the issues is that ID shows something different from a VC terminal and from a GUI:
from VC terminal:
```

$ id
uid=1000(username) gid=1000(username) groups=4(adm),20(dialout),24(cdrom),46(plugdev),100(users),112(lpadmin),113(sambashare),114(admin),1000(username)

```
from the gui terminal:
```

$ id
uid=1000(username) gid=1000(username) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),113(sambashare),114(admin),1000(username)

```
Somehow running a gui masks out group membership in the users group only and not other groups.

Any ideas why? Should I change user to be the primary group instead of username?

Also, the .Xauthorization file for my GUI session is blank, not sure if that could be related.

---

### Post by sloggerkhan on 2009-03-01
SOLVED. 
Not 100% sure how, but no longer have issue.

---

