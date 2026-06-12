---
title: "What does adding &quot;-a&quot; do?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by jrd on 2006-06-28
Command -a. <<<What does that do? Also what is that called, it's not a command so what is it? I tried looking it up but didn't know what to call it.

---

### Post by aysiu on 2006-06-28
It's not a command. It's an option added to commands. For example, in this command ```
sudo mount -a
``` *mount* is the actual command. *sudo* escalates the privileges of the command to be that of the administrator. *-a* is just an extra parameter.

From ```
man mount
``` > -a     Mount all filesystems (of the given types) mentioned in fstab.

---

### Post by jrd on 2006-06-28
Thanks for the help aysiu. I tried looking in the man pages for "-a" but that didn't bring much up, lol. Thanks again.

---

### Post by mcduck on 2006-06-29
No, tou still got it wrong. '-a' is not a command, so there is no manual page for it.

Some programs take extra parameters, for example the command 'free' tells you about your memory usage, and if you do 'man free' you'll find out that you can run 'free -m' to get output from free as megabytes instead of bytes.

In a same way you can run 'glxgears' to test if your 3D acceleration works fine, and 'glxgears -iacknowledegethatthistoolisnotabenchmark' to make glxgears output frames/second info.

Or the 'dpkg'-command used to install .deb packages. 'dpkg -i <packagename> will install a package, while 'dpkw -r <packagename> will uninstall it.

What parameters a command has depends on the command. So there are no 'global' parameters, each command has it's own.

---

### Post by hayesey on 2006-06-29
any option given to a command can mean a different thing with each command.

E.G. *mount -a* and *grep -a* in the first instance the '-a' tells mount to "mount all" but in the second instance the '-a' sets the binary file type to text.

In all cases, look at the 'man' page for the command in question to see what '-a' means when used with a particular command.

---

### Post by jrd on 2006-06-29
Thanks

---

