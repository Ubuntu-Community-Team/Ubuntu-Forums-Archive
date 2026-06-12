---
title: "Not in sudoers, and can't get in"
date: 2005-08-22
forum: Desktop Environments
---

### Post by ree on 2005-08-22
After my problem with not being able to fix the time ([this thread](http://ubuntuforums.org/showthread.php?t=58661) and trying to fix it with kcontrol, I've run into a similar problem trying to add myself (the first and only user account, which I thought should be in sudoers by default) to sudoers, using the instructions at [http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers).  However, like I did with the kcontrol command, I get the same(ish) bunch of error messages when trying to use "visudo" (below).  Therefore, I can't add myself to sudoers, and as a consequence, can't change practically anything on my OS.  I'm using Kate instead of gedit, since I'm running a default Kubuntu install.

Can anyone help with this?  I'm nearly reaching for another distro at this point, yet I'm sure this can be salvaged somehow.  TIA

```
root@SPANKY:/home/ree # export EDITOR=kate && sudo visudo
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-8879' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-8869' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.
visudo: sudoers file unchanged
```

---

### Post by codejunkie on 2005-08-22
[QUOTE=ree]After my problem with not being able to fix the time ([this thread](http://ubuntuforums.org/showthread.php?t=58661) and trying to fix it with kcontrol, I've run into a similar problem trying to add myself (the first and only user account, which I thought should be in sudoers by default) to sudoers, using the instructions at [http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers).  However, like I did with the kcontrol command, I get the same(ish) bunch of error messages when trying to use "visudo" (below).  Therefore, I can't add myself to sudoers, and as a consequence, can't change practically anything on my OS.  I'm using Kate instead of gedit, since I'm running a default Kubuntu install.

Can anyone help with this?  I'm nearly reaching for another distro at this point, yet I'm sure this can be salvaged somehow.  TIA

```
root@SPANKY:/home/ree # export EDITOR=kate && sudo visudo
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-8879' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-8869' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.
visudo: sudoers file unchanged
```[/QUOTE]

can you login as root with the command ```
sudo su
```and entering your password when prompted?
edit: the reason i asked this is when some one usually asks about switching to the root user in ubuntu i've noticed someone here usually just tells them something like > ubunt uses sudo and this doen't help them because they type "sudo" into a terminal not ```
sudo su
``` and they still continue to get error messages.

---

### Post by ree on 2005-08-22
[QUOTE=codejunkie]can you login as root with the command ```
sudo su
```and entering your password when prompted?[/QUOTE]
Nope :(
> ree is not in the sudoers file.  This incident will be reported.

I can "su root" and enter the root password (correctly), though.

---

### Post by codejunkie on 2005-08-22
[QUOTE=ree]Nope :(


I can "su root" and enter the root password (correctly), though.[/QUOTE]
ok you must have done an expert install instead of a default and enabled the root password just su to root and then run the command to edit the sudoers file.
export EDITOR=kate && visudo

---

### Post by ree on 2005-08-22
[QUOTE=codejunkie]ok you must have done an expert install instead of a default and enabled the root password just su to root and then run the command to edit the sudoers file.
export EDITOR=kate && visudo[/QUOTE]

Thanks so much!! That did it :)

(happy once again! \\:D/)

---

