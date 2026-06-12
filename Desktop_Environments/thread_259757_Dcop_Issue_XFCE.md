---
title: "Dcop Issue XFCE"
date: 2006-09-17
forum: Desktop Environments
---

### Post by KeeganX on 2006-09-17
I installed the XFCE 4.4 RC1 and I cannot load any KDE apps.  It says something about dcop or something like that.  I have no clue what that is but I believe it has somethign to do with KDE applications.  If anyone knows how to put dcop back on or the solution to this problem please let me know. thanks.

---

### Post by orb9220 on 2006-09-17
If you want a lighter-weight version of KDE, do 
sudo aptitude install kde-core
which is required to run kde apps. Info from: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

When you install kde app from synaptice it should have installed this automatically.

---

### Post by KeeganX on 2006-09-18
It seems if I run the KDE apps in sudo mode they run perfectly fine... Is there a way to change how its launched in the menu editor?

---

### Post by kuja on 2006-09-18
You would have to change it for each and every kde app, and, mind you, that wouldn't be a particularly optimal (nor secure) solution anyhow. one potential, though odd, solution for you might be to

Create a new user account

First, log out, and log into a console session. Then run (some variant of) these commands.
```

adduser billybob
su - billybob
startx

```

If this fixes the problem for you, then perhaps you are experiencing the same problem I was the other day. At any rate, here's if it does fix it, here's what to do:

- Copy all files from the old user directory to the new user directory
- Delete the old user - "*deluser --remove-home theoriginaluserlogin*"
- Re-add the old account "*adduser --gid 1000 --uid 1000 theorignaluserlogin*" **Note, 1000 is the default in an Ubuntu installation. If you have made additional accounts, make changes accordingly.

- Readd yourself to the groups that you were a member of originally:
```
sudo adduser theoriginaluserlogin adm 
sudo adduser theoriginaluserlogin dialout 
sudo adduser theoriginaluserlogin cdrom 
sudo adduser theoriginaluserlogin floppy 
sudo adduser theoriginaluserlogin audio 
sudo adduser theoriginaluserlogin dip 
sudo adduser theoriginaluserlogin video 
sudo adduser theoriginaluserlogin plugdev 
sudo adduser theoriginaluserlogin lpadmin 
sudo adduser theoriginaluserlogin scanner 
sudo adduser theoriginaluserlogin admin
```
- Copy back the files to the newly created "theoriginaluserlogin"
- Delete the temporary login "*deluser --remove-home billybob*"

---

