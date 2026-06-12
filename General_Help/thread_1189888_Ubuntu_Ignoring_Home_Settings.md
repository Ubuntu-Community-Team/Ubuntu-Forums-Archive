---
title: "Ubuntu Ignoring Home Settings?"
date: 2009-06-17
forum: General Help
---

### Post by aglc2005 on 2009-06-17
I restarted my computer and upon logging back in, Ubuntu informed me that my home folder should be private and that is should be 664 and that the default session would be ignored. What do I need to do to restore this? Anyone have a suggestion as to how this happened? I'm running 64-bt Jaunty.

---

### Post by Celauran on 2009-06-17
Any way for you to post the exact error? Setting ~ to 664 doesn't sound right.

---

### Post by mhgsys on 2009-06-17
Am I wrong to think that this is the error message?:
```

"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users."

```
If so ; I've seen that error before and fixed it with the following commands. 

You should try this.

```

sudo chmod 644 /home/username/.dmrc

```

```

sudo chown username /home/username/.dmrc

```

```

sudo chmod 755 /home/username

```

*replace username with your username ofcourse.
reboot, 
all should be working.

---

### Post by nola504 on 2009-06-21
Seems like the .dmrc issue is related to granting too much permission to 'everyone' on your home folder.

In many cases setting your home folder to 755 will not fix the problem and is also pretty invasive being that you are mangling existing permissions such as which files are executable and what not.

The best way to solve this issue is to issue the following commands:
```
sudo chown -R username:username ~/
sudo chmod -R o= ~/
sudo chmod 644 ~/.dmrc
```

The first command is simply making sure you own all the files in your folder (don't forget to change 'username' to your actual username). You might receive the error 'Permission denied' for the .gvfs folder. This is fine you can ignore it.

The second command removes all permission for 'everyone'. This means that only you can access your files which is what that .dmrc error is really complaining about. This command is less invasive because you are preserving your existing permissions assigned to you. A good thing. However, if you've already been playing around with permissions on your home folder you may have to resort to the more drastic 750.

The third command makes sure you have write permission to your .dmrc file.

Hope this helps someone.

---

