---
title: "Opening executables as Text files."
date: 2010-10-29
forum: Desktop Environments
---

### Post by nagisa on 2010-10-29
So I have Python file :
```

#!/usr/bin/env python
print 'python'
raw_input('')
```
And another : 
```

#!/usr/bin/python
print 'python'
raw_input('')
```
Both they are with 777 permisions
Before I reinstalled Ubuntu (From 10.10 to 10.10), I always got prompt window to run it in either Terminal, standalone or open as text file.
Now it just opens it as text file(Octal Permissions 100777, In preferences->Behavior it's set to Ask each time.)

From terminal running it using this :
```
/media/sda3/Python/python.py
```
Prints : 
```
bash: /media/sda3/Python/python.py: Permission denied
```
And using this :
```
python /media/sda3/Python/python.py
```
prints :
```
python
<Waiting input>
```
as it should. I don't want to take such a hassle always running python by path. P.S. I'm still newbie at Ubuntu.

---

### Post by 3Miro on 2010-10-29
What kind of disk is sda3 (internal/external). How are you mounting it. What are the permissions and ownership of all the olders going to /media/sda3/Python/your_file.py?

It is possible that the HDD is mounted with flags that prevent any program from executing. This is in addition and independent from the regular 777 permissions. When you call
```
 python your_file 
```
the executable is "python" and your file is just being read as input. In the case of
```
 ./your_file 
```
then your file is the executable itself.

---

### Post by nagisa on 2010-10-29
It's just another partition on same disk.
sda1 - linux partition
sda3 - media partition
sda5 - swap
I used Storage Device manager to configure my partitions, so I took screenshots of it.
fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=09f82d30-3d88-492a-941d-aa39081f389c  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=6e3bbc18-05b9-4dc2-aa8c-674ecd073478  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda3                                  /media/sda3     ext4  users,user                0  0  
```
BTW: I grabbed on idea I catched from your post : .py files that I paste on desktop works fine.

---

### Post by 3Miro on 2010-10-29
In your fstab file, you should add "exec" option to /dev/sda3 to allow files inside to be started as executables. You can also change the "users,user" to defualts, which I think includes all of the above. I have four partitions, all of them use defaults and I can execute files from all.

---

### Post by nagisa on 2010-10-29
> **3Miro said:**
> In your fstab file, you should add "exec" option to /dev/sda3 to allow files inside to be started as executables. You can also change the "users,user" to defualts, which I think includes all of the above. I have four partitions, all of them use defaults and I can execute files from all.

Thanks, default solved it all.

---

