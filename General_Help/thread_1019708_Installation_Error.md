---
title: "Installation Error"
date: 2008-12-23
forum: General Help
---

### Post by linuxmiller on 2008-12-23
Whenever I try and install any software, this message comes up:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Do you know why that is?


Also, how do you logon to the root user, it won't let me in the startup screen.

---

### Post by taurus on 2008-12-23
Close add/remove or update-manager first if you have one open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

You do not need to log in as root.  Use sudo to give yourself root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by redilyn on 2008-12-23
In Ubuntu you do not login as root. You use the sudo or gksudo command instead.

If you insist on running as root you can open a root prompt by typeing the following in a terminal

```

sudo -s

```

---

### Post by decoherence on 2008-12-23
ubuntu has no root user. if you wish to gain root in a terminal, use sudo.

if you want to run graphical programs as root, press alt F2 and type "gksudo name-of-program"

if you want to enable root, simply set a password

"sudo passwd root"

I believe you will also have to make a change to GDM's configuration to allow root logins from the GUI. I believe the file you need to edit is /etc/gdm/gdm.conf and set 'AllowRoot' to 'true' or something like that. I'm not in front of an ubuntu machine right now so i'm not sure.

you probably shouldn't enable it, though. just get used to sudo-ing.

---

### Post by linuxmiller on 2008-12-23
> **taurus said:**
> Close add/remove or update-manager first if you have one open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

You do not need to log in as root.  Use sudo to give yourself root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

First of all, thanks for such a quick response.
Secondly, I can paste the code into Terminal, but then it doesn't let me put my password in.
Thanks.

---

### Post by redilyn on 2008-12-23
Someone else just had this problem recently. To get around it do the following

```

sudo -s

```

Enter your user password and press enter. You should now have a root prompt.

Then do


```

dpkg --configure -a

```

That should fix it so you can add/remove programs again.

You shouldn't have to run apt-get update or apt-get dist-upgrade, it shouldn't be necessary unless you want to check for updates and then upgrade your installation.

---

### Post by linuxmiller on 2008-12-23
Hi.

It will let me type and paste, but when I get to my password, the only thing I can do is press the return key.

Thanks for all the help so far.

---

### Post by redilyn on 2008-12-23
Okay, There will be no feedback when you try to type your password.

Just type the correct password when it asks and press enter.

You will not see any * or anything

---

### Post by bobbyg234 on 2008-12-23
I have a similar trouble. Same error:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

When typing command [COLOR="Blue"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR] from root I get the following error:

"dpkg: parse error, in file `/var/lib/dpkg/updates/0024' near line 1:
 field name ' must be followed by colon"

Any help would be appriciated. Thanks.

---

### Post by bobbyg234 on 2008-12-23
Oops. The command I used and recieved the above error was
[COLOR="Blue"]dpkg --configure -a[/COLOR]

---

### Post by redilyn on 2008-12-23
Probably a corrupt file.

```

cd /var/lib/dpkg/updates
rm *

```

You might have to run the rm command with sudo. I can't check because that dir is empty on my system.

---

### Post by bobbyg234 on 2008-12-23
*FIXED* Deleting [COLOR="Blue"]/var/lib/dpkg/updates[/COLOR]worked. Still learning the commands. Much thanks.

---

