---
title: "User customization lost after disk full"
date: 2014-05-30
forum: Desktop Environments
---

### Post by mmulqueen on 2014-05-30
Hi all,

I'm not terribly familiar with Ubuntu but one of my users recently had some trouble with his Ubuntu machine that I can't find an explanation for.  I'm hoping someone here can shed some light on this mystery.  The user runs a daemon on his PC that filled the root partition and didn't know how to act once it encountered write errors.  His home directory is on a different disk but he was still unable to login using the KDE interface.  I had an SSH session up, so I cleared out ~70GB of temporary files that weren't needed and the daemon had failed to remove because it crashed.  The user rebooted the machine after I cleared the files. I'm trying to figure out why he was still unable to login after the reboot.  I dug around in the logs and found permissions errors creating files for the X session in the user's home directory and, when I did ls -l on his home directory, I found his home directory owned by root.root.  So this is why he still couldn't login but....how did this happen?  The ownership change was not done recursively.  I just gave the directory back to him and he was able to login.  Now, he says that none of his UI customizations are there anymore.  I verified this.  All of the user specific historical and config files under his directory are gone....bash_history, .bash_rc, .cache, .config, .profile, .zshenv, .zshrc are all gone.  I was thinking, there's no way that this is the behavior of the OS when the root partition is filled, so I checked all the other users' bash history for anything done to his home directory and for unauthorized logins but found no evidence that this was done on purpose.  Is there some built-in logic that would cause this?

Thanks,

Matt

---

### Post by TheFu on 2014-05-31
That daemon .... who wrote it?  I think it has a bug (probably more than 1) and if run as root, it it probably tweaking $HOME.  Was the entire HOME cleared or just the .dotfiles?

Anything happen to other users HOMEs?

BTW, users should still be able to login even without write to HOME ... er ... unless they have something in their login script that mandates it and is failing.

---

### Post by mmulqueen on 2014-06-02
The user wrote the daemon, which runs under the user's login.  It just checks out and builds newly checked in code and doesn't require any root privileges.  All of the user's data was intact.  It was just the .dotfiles that were deleted.  Other users' $HOME directories were not touched.  Here are the errors from the syslog that made me think to check permissions on the user's $HOME.

May 30 15:26:14 glass kdm: :0 '[2859]: Cannot update authorization file in home dir /home/user
May 30 15:26:14 glass kdm: :0 '[2859]: Session log file according to .xsession-errors cannot be created: Permission denied

Thanks,

Matt

---

### Post by TheFu on 2014-06-02
There is no end to what damage buggy code can cause. If the user is the creator, then she/he should be able to debug and fix it.

Those are X/Windows related errors. I have no idea how the ownership changed from the normal userid to root, but X likes to have a few files in ~/ that can be added/appended and possibly created.  Logging in without using X will help to determine if that is the sole issue or not.

At this point, I'd mark this as user-error and move on.  The programmer can modify the code to perform logging of every step, which will help him/her figure out their code error, lacking any more information.

Or the box has been hacked. That is always an option especially when end-users are allowed logins on systems. I don't think this is likely, but just something to consider.

---

### Post by mmulqueen on 2014-06-03
Thanks for the help!

---

