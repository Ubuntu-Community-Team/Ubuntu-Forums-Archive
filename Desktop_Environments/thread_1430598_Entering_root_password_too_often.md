---
title: "Entering root password too often"
date: 2010-03-15
forum: Desktop Environments
---

### Post by JNied on 2010-03-15
I'm sorry, I'm not sure if this is in the right forum.

There are a lot of things I do on my system that require root access.  For example, my text editor, because sometimes I want to edit config files and what not.  My root terminal, so that I can run administrative commands and the likes, and so on.

However, I find myself having to enter my root password far to often.  I even have to enter it when shutting down or rebooting, because it says that root password is required when shutting down while other users are logged in.  I only have one user on the computer, so I don't know why I have to enter my password every time I want to shut down.

In any case, is there a way that I can enter the root password when I first log in and not have it ask me again?

Any help would be greatly appreciated and I thank you in advance.


In case it helps: ```
root@Jason-Ubuntu:/# uname -a
Linux Jason-Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
```

---

### Post by RasterBurn on 2010-03-15
i know what you mean, sometimes there is just too many times to put in a password, although its part of the security system in Linux you can disable some of it though you should be careful while disabling things, one thing to look at is the keyring you should be able to tell it to not ask for a password to run the app as root, if you are good at programming you could write a script that sets your uid to root upon unlocking the keyring for the first time of that session, I would recomend against bypassing the security as much as possible, you might have more issues with intrusive Linux malware kicking up a storm on your computer without your knowledge of it being there.. I personally would not advise fully unlocking your account to run as root though if you feel ambitious enough, make a list of the root programs you most commonly use and make gksu links for each one and then make a link that unlocks your keyring for that session (that is if the programs are GUI, use shell scripts for programs that are CLI)

for use root permissions using the teminal i created a link in my menu with the command "gksu gnome-terminal" it asks for the password with gksu and then opens my terminal as root user :)

---

### Post by fancypiper on 2010-03-15
Try adding yourself to the sudoers group and edit your /etc/sudoers file to read thusly:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults<------>env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root<-->ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%sudo ALL=NOPASSWD: ALL

```

HTH

---

### Post by wojox on 2010-03-15
When you shut down from the GUI it asks for a password?

---

### Post by aysiu on 2010-03-15
The really simple way to deal with this is to use ```
sudo -i
``` This gives you a persistent root prompt.

If you're using a graphical application, use *gksudo*. For example: ```
gksudo nautilus
``` or ```
gksudo gedit
```

---

