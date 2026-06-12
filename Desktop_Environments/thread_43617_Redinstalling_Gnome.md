---
title: "Redinstalling Gnome"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-22
My brother is running Ubuntu. He rebooted his computer one day and can no longer get into gnome. He can get to the Ubuntu login screen, and X server starts. He can get a failsafe terminal to work as well. However, gnome does not work.

What would the command be to reinstall gnome or configure its default settings? Thanks!

---

### Post by Xian on 2005-06-22
Don't have an exact answer for you.....

However, you should be able to reinstall the system with the command below.
But note that you have to run it as su. The 'sudo' command is not sufficient.

If you need to setup a root password to run su then issue the command below.
It will ask you to enter and confirm a root (Unix) password.

```
$ sudo passwd
```
To reinstall the system with this method you will need to make sure that all installed packages are able to be downloaded using the sources list. If you have downloaded and installed some deb files off the net that are not available via Synaptic then this will not work. They will first have to be removed or given access to Apt by any number of various methods by creating local repos. In addition, there can be no broken packages on the system.

If the system files are cached (which is the default) the nothing should need to be downloaded. Everything will be built from the local apt cache.

```
$ su
$ dpkg --get-selections | egrep '[[:space:]]install$' | cut -f 1 | xargs apt-get install --reinstall
```

---

### Post by Curlydave on 2005-06-22
when I do "su", it says "authentication failure, sorry. [you can blow me because you're not allowed to do shit, hahahaha!! nice try, sucka!]"

---

### Post by Xian on 2005-06-22
Reset the root password again and post the output from the terminal:
```
$ sudo passwd
```
It should look like this:
```
$ sudo passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```
EDIT: Oh, and please set your root/unix password to something
 that is NOT your user/sudo password.

---

### Post by Curlydave on 2005-06-22
ohh, ty. But now it's pulling that can't find restricted backport something-or-toerh thing and I need to apt-get update to fix it. I apt-got updated it and it did many things, not including fixing the error if I ran the command again.

---

### Post by Xian on 2005-06-22
[QUOTE=Curlydave]ohh, ty. But now it's pulling that can't find restricted backport something-or-toerh thing....[/QUOTE]
Most likely that is the occurance I was telling your about where there is a package version installed that is no longer available in the source.list repos or local cache. You can post the exact error message if you want me to look at it and be certain. Can you just remove the offending package without upsetting the system and then reinstall the same after the system rebuild?

---

