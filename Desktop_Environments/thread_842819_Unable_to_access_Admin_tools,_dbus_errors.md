---
title: "Unable to access Admin tools, dbus errors"
date: 2008-06-27
forum: Desktop Environments
---

### Post by bobstro on 2008-06-27
I am having problems with (apparently) dbus when launching some Admin tools. If i run, for example, **System->Administration->Users and groups** or **Network**, I get a dialog box with "The configuration could not be loaded. You are not allowed to access the system configuration." 

If I run **users-admin** at a shell prompt, i get "Failed to execute program /usr/lib/dbus-1.0-/dbus-daemon-launch-helper: Success" at the shell prompt, then the same dialog box.

If I run **gksudo users-admin** in gnome, I am prompted for my password (as expected), then get the same dialog box message.

If I run **System->Administration->Printing**, I am repeatedly asked for my password.

Somebody mentioned that a mismatched /etc/hosts and /etc/hostname could cause this. I have compared this machine's configuration to another working box, and they are the same:
> 
bob@hostname:~$ hostname
hostname.domain.com
bob@vmware02:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.0.1    hostname.domain.com hostname
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

$ uname -a
Linux hostname.domain.com 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

**Update manager **works fine.

This all started as an attempt to fix removable USB flash drives not mounting automatically, when I realized I couldn't edit user rights from the GUI.

Everything had been working until a few days ago. The only significant system change I can recall was applying the latest updates. I have tried the original kernel (2.6.24-17) as well as newer (2.6.24-19). 

Any help much appreciated!

Thanks,

- Bob

---

### Post by abackstrom on 2008-10-16
I had this problem today. It turned out to be bad permissions on [FONT="Courier New"]/usr/lib/dbus-1.0/dbus-daemon-launch-helper[/FONT]. A chmod fixed the problem, after verifying the file was setuid root on another system. Here's the known-good box:

```
adam@adam-desktop:~$ ls -l /usr/lib/dbus-1.0/
total 228
-rwsr-xr-- 1 root messagebus 228628 2008-05-14 21:45 dbus-daemon-launch-helper
```

Here's the fix on the bad box:

```

sudo chmod 4754 /usr/lib/dbus-1.0/dbus-daemon-launch-helper
sudo chown root:messagebus /usr/lib/dbus-1.0/dbus-daemon-launch-helper

```

I have no idea what caused it. It's on my wife's laptop, and she does not delve into the command line. Might have been one of the package updates.

**Update:** The laptop had some problems the next day, so I compared the permissions again and noticed the group ownership was wrong. I did an o+x on that machine which probably isn't the best fix. Updating this post with group ownership info.

---

