---
title: "Error when updating software"
date: 2006-07-13
forum: Desktop Environments
---

### Post by chloraldo on 2006-07-13
I got the message that there is new software to update. As usual I tried to update. This time it didn't work. I got this message:
```
Software index is broken

It is impossible to install or remove any software.
Please use the package manager "Synaptic" or run
"sudo apt-get install -f" in a terminal to fix this
issue at first.
```

I tried sudo apt-get install -f but got this message:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 113080 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any help?

---

### Post by OptikKnight on 2006-07-13
I'm having the same issue. There's already another thread started on the topic, but no solutions or recommendations found yet.

---

### Post by chenel on 2006-07-13
> **chloraldo said:**
> I got the message that there is new software to update. As usual I tried to update. This time it didn't work. I got this message:
```
Software index is broken

It is impossible to install or remove any software.
Please use the package manager "Synaptic" or run
"sudo apt-get install -f" in a terminal to fix this
issue at first.
```

I tried sudo apt-get install -f but got this message:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 113080 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any help?


Delete the /etc/rc2.d/K09samba symlink and re-run apt-get install -f.  That should do it.

---

### Post by Xwild on 2006-07-13
> **chenel said:**
> Delete the /etc/rc2.d/K09samba symlink and re-run apt-get install -f.  That should do it.


Worked for me.  Thanks.

---

### Post by chloraldo on 2006-07-14
> **chenel said:**
> Delete the /etc/rc2.d/K09samba symlink and re-run apt-get install -f.  That should do it.
Thanks, worked!

---

### Post by meenfreem on 2006-07-14
> **chenel said:**
> Delete the /etc/rc2.d/K09samba symlink and re-run apt-get install -f.  That should do it.

and what would the terminal line be to delete that particular symlink? I'm pretty new with all this and the only response I get is that that file does not exist :S

---

### Post by philippe_carlo on 2006-07-14
```
sudo rm -f /etc/rc2.d/K09samba
```

---

### Post by chenel on 2006-07-14
> **philippe_carlo said:**
> ```
sudo rm -f /etc/rc2.d/K09samba
```
If that doesn't work, then your symlink might be in a different place (everybody else's has been the one mentioned here but that doesn't mean yours has to be, I guess).  First run
```
sudo apt-get install -f
```
and look for a line that says something about a 'dangling symlink' (see first post in this thread).  Then do what philippe_carlo says for whichever symlink is reported.  Hopefully that'll fix the problem.

-chenel

---

### Post by ras on 2006-07-14
Just confirming that deleting /etc/rc2.d/K09samba as suggested in this thread worked for me.

-ras

---

### Post by meenfreem on 2006-07-17
it seemed to have worked, although indeed for me there was a different dangling symlink... S91samba... but updates are working again! Thanks!

ps. turned out i missed the -f in the command :S

---

### Post by chenel on 2006-07-17
> **meenfreem said:**
> it seemed to have worked, although indeed for me there was a different dangling symlink... S91samba... but updates are working again! Thanks!

ps. turned out i missed the -f in the command :S

word.  Glad it worked.

-chenel

---

