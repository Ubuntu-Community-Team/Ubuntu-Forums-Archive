---
title: "I'm not admin? Can't access sudo."
date: 2009-05-03
forum: General Help
---

### Post by HydroTech on 2009-05-03
Hey, I'm having almost the same problem. I can't access anything that requires sudo. I can't access synaptic package, users and groups, usw... The thing is, I used to be able(with my password) to access anything I wanted but not now. It always says 'Failed to run 'x' as system root'. Then underneath, it says something about sudo mechanism does not allow you to run this program. Contact the Admin. I am the admin!lol As it is, in my account, I can't edit sudoers file. Any ideas?
One more thing: does it matter that I installed a new graphics card a little while back? It hasn't worked to good so far. Only in 'Low Graphics Mode'.

Thanks!

---

### Post by spiderbatdad on 2009-05-03
You should be able to boot from the live cd and mount your file system. Then look at /etc/sudoers and add yourself.
Open terminal from live cd:
```
sudo fdisk -lu
sudo mount /dev/**sdaX** /mnt #where sdx is actually sda1 or sdb2, etc.
sudo select-editor #should allow you to select nano...easier than vi for new users.
sudo nano /etc/sudoers

```
Ctrl+o to save...enter to confrim...ctrl+x to exit.

The default file should look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Some kernels will return an error with the above mount command and request a mount option:
in which case the command will be like:
sudo mount -t ext3 /dev/sdaX /mnt
for ext3 filesystems.

---

### Post by HydroTech on 2009-05-03
ok, I was able to boot into my original ubuntu 8.10 install and I mounted, used nano to edit sudoers. What exactly should I edit? Everything is almost the same as your example. My username never appeared in there.

---

### Post by HydroTech on 2009-05-03
Also, what do you think I could be doing to cause this issue? I haven't played with any root settings.

---

### Post by michy99 on 2009-05-03
You didn't by any chance create a user named admin did you? There is a bug which will delete the admin group if you do and prevent users from having administrative privileges.

---

### Post by cariboo on 2009-05-03
Here is my copy of the default /etc/sudoers, compare it with yours and make changes as needed.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by jowilkin on 2009-05-03
Ubuntu is set up to grant everyone in the admin group sudo rights.  So first thing you may want to check is if you are in the admin group. To do this just type
```
id
```
It should show you your uid, gid, and all groups that you belong to. If "admin" isn't in the list of groups, that's your problem.

---

### Post by HydroTech on 2009-05-04
Okay, thanks guys,
I'll try these things tonight when I get a chance and I'll get back with you tonight or tomorrow.
:popcorn:

---

### Post by HydroTech on 2009-05-04
> **cariboo907 said:**
> Here is my copy of the default /etc/sudoers, compare it with yours and make changes as needed.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


Now mine looks just like yours... still no admin access.

---

### Post by HydroTech on 2009-05-04
> **jowilkin said:**
> Ubuntu is set up to grant everyone in the admin group sudo rights.  So first thing you may want to check is if you are in the admin group. To do this just type
```
id
```
It should show you your uid, gid, and all groups that you belong to. If "admin" isn't in the list of groups, that's your problem.

I typed id:
"uid=1000(josh) gid=1000(josh) groups=25(floppy),1000(josh)"
I'm not in admin group. How do I add myself to it?

---

### Post by michy99 on 2009-05-04
What does your etc/group file look like?

---

### Post by HydroTech on 2009-05-04
Nothing in there has my name on it but floppy:
root:x 0
daemon:x 1
sys:x 3
adm:x 4
floppy x 25 josh
sudo:x 27

I had to edit it down to this b/c the forum won't allow ' over 8 images.'

---

### Post by HydroTech on 2009-05-04
overlook the pics. couldn't get rid of them.

---

### Post by Don1500 on 2009-05-04
> **HydroTech said:**
> Hey, I'm having almost the same problem. I can't access anything that requires sudo. I can't access synaptic package, users and groups, usw... The thing is, I used to be able(with my password) to access anything I wanted but not now. It always says 'Failed to run 'x' as system root'. Then underneath, it says something about sudo mechanism does not allow you to run this program. Contact the Admin. I am the admin!lol As it is, in my account, I can't edit sudoers file. Any ideas?
One more thing: does it matter that I installed a new graphics card a little while back? It hasn't worked to good so far. Only in 'Low Graphics Mode'.

Thanks!
From ROOT
System > Administration > Users and Groups > "Josh" > Properties > User Privileges > Give yourself Admin Privileges.  :P:

"How do I get to ROOT?" I can't tell you that! (But you're close)  :wink:

---

### Post by HydroTech on 2009-05-04
it won't allow me access to users and groups.

---

### Post by michy99 on 2009-05-04
I had a similar problem, and this is what i did. No guarantees.

Boot from Live CD.

Create mount point for hard drive partition:
```
sudo mkdir /media/drive
```

Mount drive:
```
sudo mount -t ext3 /dev/sda1 /media/drive
```

This assumes that your Ubuntu partition is ext3 and located on sda1. You may have to adjust it.

Make backups of your /etc/group and /etc/gshadow files:
```
cd /drive/etc
sudo cp group group.backup
sudo cp gshadow gshadow.backup
```

Now copy the files from the Live CD:
```
sudo cp /etc/group group
sudo cp /etc/gshadow gshadow
```

Now open group:
```
gksudo gedit group
```
and everywhere it says 'ubuntu' replace it with your username. Save and exit.

Open gshadow
```
gksudo gedit gshadow
```
and do the same thing. Save and reboot to your hard drive.

Good luck. It worked for me.

---

### Post by HydroTech on 2009-05-05
I just tried it. It didn't fix a thing. Great idea though. *sigh*
I guess I will go to bed right now. At worst, I'll reinstall with ubuntu 9.10 jaunty jack. hate to though b/c it will probably do the same thing after a while. :confused:

---

### Post by paradigm2 on 2009-05-05
Try using recovery mode to get in as root.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Then:

```

adduser josh -G adm

```


Then 

```

shutdown -r now

```

And give it a go.

---

### Post by jowilkin on 2009-05-05
What does it say when you type id now?  I have a feeling you only modified the files that the live cd was using when you tried the procedure mentioned by michy, you needed to modify the files in /media/drive/etc, not the ones in /etc.  The ones in /etc were only being used by the live cd and were lost when you rebooted into your normal environment.

This is not a common problem, I wouldn't worry about it happening again.  Going into recovery mode as suggested and adding yourself to the admin group is a good way to get sudo rights working again.

---

### Post by HydroTech on 2009-05-06
okay, I'm trying it...
Still says I'm not allowed.
Trying id...
id: uid=1000(josh) groups=25(floppy),1000(josh)

I guess I'll bootup in livecd and try editing the right folder.LOL...

---

### Post by HydroTech on 2009-05-06
Well boys and girls, you've done it again!!!!!!!!
It worked!!!!!!!!!!!:KS:KS:KS:KS:KS
I just replaced the sda1 group and gshadow files with liveCD equivalents and edited everywhere it said 'ubuntu' with my username and voila! it worked. Thanks so much!

---

