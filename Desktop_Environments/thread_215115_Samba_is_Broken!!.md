---
title: "Samba is Broken!!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by benclinch on 2006-07-13
Hi...
Since I upgraded from 5.10 to 6.06 (automatically through the update program) I have kept getting error messages because of samba. Now, I don't use samba, I don't need it (or do I??). But now theupdate manager up there^^ won't work. I have the little orange star telling me updates are ready. When I Show updates it comes up with an error message "Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."
I did the sudo, no difference. I go in Synaptic and use the filter for broken things. And up pops Samba. Whenever I usse Add/Remove, it installs everything fine, but always comes up with an error message at the end:
Error.
The following problems were found on your system.
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102


Basically, I don't think that Samba installed when I updated, but it thinks it has, and wants to find it!!!
Please help this is really getting on my nerves now!
Any help is appreciated.

Ben ](*,) (<<me)

---

### Post by OptikKnight on 2006-07-13
Hey, did you get this fixed? I just encountered the same issue on my 6.06 installation. Any tips would be helpful... I tried deleting the upgraded .deb  from /var/cache/apt/archives and still no luck. I'm not familiar enough with Apt to debug it myself.

---

### Post by chenel on 2006-07-13
> **benclinch said:**
> Hi folks...
Since I upgraded from 5.10 to 6.06 (automatically through the update program) I have kept getting error messages because of samba. Now, I don't use samba, I don't need it (or do I??). But now theupdate manager up there^^ won't work. I have the little orange star telling me updates are ready. When I Show updates it comes up with an error message "Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."
I did the sudo, no difference. I go in Synaptic and use the filter for broken things. And up pops Samba. Whenever I usse Add/Remove, it installs everything fine, but always comes up with an error message at the end:
Error.
The following problems were found on your system.
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102


Basically, I don't think that Samba installed when I updated, but it thinks it has, and wants to find it!!!
Please help this is really getting on my nerves now!
Any help is appreciated.

Ben ](*,) (<<me)

First run sudo apt-get install -f (the same idea as the 'broken packages' filter in Synaptic).  You should get a message about a 'dangling symlink' somewhere.  Delete this symlink, run apt-get install -f again, and it should go.

-chenel

---

### Post by cptnapalm on 2006-07-13
The frequency of problems with pre/post removal scripts is the one weakness which apt has and which I think needs to be looked into by the apt people.  Really broken packages can irritate like little else.

---

### Post by boxarocks on 2006-07-13
I tried running '[COLOR="Red"]sudo apt-get install -f samba[/COLOR]' and the results are below. Of course I was up late last night trying to get Ubuntu to see my WinXP shared folders (lots of tweaking) so I wonder if I may have broken something else all by myself?

sudo apt-get install -f samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 93804 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
Unpacking replacement samba ...
Error installing new /etc/inetd.conf: Operation not permitted
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Error installing new /etc/inetd.conf: Operation not permitted
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Error installing new /etc/inetd.conf: Operation not permitted
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by OptikKnight on 2006-07-13
OK, Doing the "sudo apt-get install -f" business didn't work. It complains of a broken software index. Looking around a bit more, I found a better solution:

```
sudo aptitude purge samba
```

and then 

```
sudo apt-get install samba
```

It still complained a little, but nothing significant after that.

Good luck!

---

### Post by chenel on 2006-07-13
> **OptikKnight said:**
> OK, Doing the "sudo apt-get install -f" business didn't work. It complains of a broken software index. Looking around a bit more, I found a better solution:

```
sudo aptitude purge samba
```

and then 

```
sudo apt-get install samba
```

It still complained a little, but nothing significant after that.

Good luck!

Well... apt-get install -f won't fix the problem by itself anyway: you need to do it to figure out which symlink to erase.  Once you erase the symlink, apt-get install -f will finish installing samba (without the need to completely uninstall it first).  But your method (although a bit heavy-handed... needs to uninstall and then reinstall) works too.

boxarocks: I have no idea... it almost sounds like you don't have appropriate permissions -- but if you run it with 'sudo' that shouldn't be possible!  You might try 'completely uninstalling' samba (which will erase your config files), but that's a last-ditch solution...

-chenel

---

### Post by boxarocks on 2006-07-14
One last try before I completely uninstall samba:

```
~$ [COLOR="Red"]sudo aptitude purge samba[/COLOR]
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be automatically REMOVED:
  samba{p}
The following packages have been kept back:
  xserver-xorg-core
The following packages will be REMOVED:
  samba{p}
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 7250kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing samba (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
~$ Errors were encountered while processing:
 samba
```

---

