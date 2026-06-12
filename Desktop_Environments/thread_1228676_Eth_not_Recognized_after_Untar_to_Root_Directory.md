---
title: "Eth not Recognized after Untar to Root Directory"
date: 2009-08-01
forum: Desktop Environments
---

### Post by huangyingw on 2009-08-01
hello,
    I am experimenting how to back and restore a ubuntu system.
    While I met some problem after restoring.
    I used following code to backup:
    ```

#!/bin/bash

x=`echo $0 | grep "^/"`

if test "${x}"; then
	script_path=$(dirname "$0")
else
	x=`echo $0 | sed -e 's/\.\///g'`
	script_path=$(dirname `pwd`/${x})
fi

tar -cvpzf ${script_path}/PrimaryStorage.backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media \
--exclude=/home/svn --exclude=/home/myproject --exclude=/root/myproject --exclude=/boot \
--exclude=/etc/network/interfaces --exclude=/etc/fstab \
    
```
    and, after backuping, I copied the *.tgz file to another totally different machine to run the following codes, trying to restore the previous machine's state to the target one:
    ```

#!/bin/bash

x=`echo $0 | grep "^/"`

if test "${x}"; then
	script_path=$(dirname "$0")
else
	x=`echo $0 | sed -e 's/\.\///g'`
	script_path=$(dirname `pwd`/${x})
fi

 tar xvpfz ${script_path}/PrimaryStorage.backup.tgz -C /
    
```
    But, after restoring, all of the things are OK,,except the the ifconfig command could not recognize my NIC..it could only recognize the lo...
    How to fix this? Should something need to be adjusted in my backup code?

---

