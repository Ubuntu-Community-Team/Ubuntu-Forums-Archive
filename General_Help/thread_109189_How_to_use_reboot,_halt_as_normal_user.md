---
title: "How to use reboot, halt as normal user"
date: 2005-12-28
forum: General Help
---

### Post by ShirishAg75 on 2005-12-28
Hi all,
      The command reboot & halt both of which are present in /sbin & are available to the su or superuser. Now I wanna use the same commands to halt or reboot also for the normal user. What should I do in order to use the commands to the normal user. Should I just copy the commands from /sbin to /bin and/or change permissions for the files mentioned. Please would like some detailed howto for the same (as noOb here.)

---

### Post by 23meg on 2005-12-28
I don't know if it's practically possible but it would be best to leave them root only. May I ask why using them with sudo doesn't help? 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by chocolatetoothpaste on 2005-12-28
just type in "sudo reboot" or whatever.  If you want to allow normal users to run them, go to the file called sudoers in your /etc folder (must be root to modify sudoers) and add this line to the end of it:

[COLOR="Red"]username[/COLOR] ALL= NOPASSWD: /sbin/reboot

replace username with the username that will run it.  This will work I think, but I haven't tested it.

---

### Post by ShirishAg75 on 2005-12-28
I tried it but didn't work. Even change the owner by chown shirishag75:shirishag75 reboot & when I do the ls -la it shows the owner as shirishag75 (the user) but still no go. It still tells me that I need to be a superuser.

---

### Post by psusi on 2005-12-28
DON'T go changing the permissions on the executable.  Just run "sudo halt".  

Anything that you need root permissions for, just prefix it with sudo.

---

### Post by ShirishAg75 on 2005-12-28
I know that have been doing that but it becomes annoyning after time. I wanna be able to just halt or reboot as normal user on the CLI as I do on the GUI. I'm sure there is a way to do that but just don't know how.

---

### Post by rcerreto on 2005-12-28
[QUOTE=shirishag75]I know that have been doing that but it becomes annoyning after time. I wanna be able to just halt or reboot as normal user on the CLI as I do on the GUI. I'm sure there is a way to do that but just don't know how.[/QUOTE]

If you're really sure about what you're doing:

chmod 04755 /sbin/halt
(from root or via sudo)

will do the trick.
From security standpoint, that's not great.
It's your computer, isn't it?  :-)

---

### Post by Refrozen on 2005-12-28
[chmod](http://manlib.com/man/166) the permissions to allow group execution, then add that file to a group your user is part of (chgrp), then use [reboot/halt](http://manlib.com/man/333) as you normally would.

---

### Post by ShirishAg75 on 2005-12-28
Thanx rcerreto, Unfortunately or fortunately I'm the only user so nobody else can do any hanky-panky. As for net would be putting up Firestarter sometime soon. But for now if this works, cool. Would sure see if I can find more about this 04 thing. Thanx once again.

---

### Post by ShirishAg75 on 2005-12-29
[quote=rcerreto]If you're really sure about what you're doing:

chmod 04755 /sbin/halt
(from root or via sudo)

will do the trick.
From security standpoint, that's not great.
It's your computer, isn't it?  :-)[/quote]

This one atleast didn't make it quite it. Infact what it did was refuse the root any access to reboot. I'm trying only with reboot now, a single executable & once successful would do the same with the other file. Would be trying the other options now.

---

### Post by ShirishAg75 on 2005-12-29
[quote=Refrozen][chmod]("http://manlib.com/man/166") the permissions to allow group execution, then add that file to a group your user is part of (chgrp), then use [reboot/halt]("http://manlib.com/man/333") as you normally would.[/quote] how do I know which group the user is part of. Would of course be reading the chmd & reboot/halt as well as chgrp man as well as info files if I can get some info. about them but if would like what u guys think/know. Would of course be cross-checking so that I understand what is written in the man, what u guys are saying & what I'm understanding :)

---

### Post by rcerreto on 2005-12-29
I tried myself and, after "chmod 04755 /sbin/halt",
entering "halt" from a common user does halt the system and "reboot" does reboot it.
Isn't that working for you?
You just have to wait for a few seconds, in the while you won't see the usual messages since the shutdown happens "behind the scene".

---

### Post by ShirishAg75 on 2006-01-01
It isn't working for me, should I see some config files or something to know if everything is alright or what?

---

