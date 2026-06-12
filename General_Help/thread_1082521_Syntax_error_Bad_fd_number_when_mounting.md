---
title: "Syntax error: Bad fd number when mounting"
date: 2009-02-27
forum: General Help
---

### Post by TCarr on 2009-02-27
I'm working on a robot development kit for the RoboSapien RS Media. Someone I know wrote a script for it that dumps the firmware and then you can browse it on any linux system by copying the files and mounting them.

Here's the mount.sh we are using:

```

#!/bin/sh

mkdir root >& /dev/null
mkdir root/mnt >& /dev/null
mkdir root/mnt/sd >& /dev/null
mkdir root/mnt/default >& /dev/null
mkdir root/lnk >& /dev/null
mkdir root/pw >& /dev/null

mount -o loop nand1 root -t cramfs
mount -o loop nand2 root/mnt/default -t cramfs
mount -o loop nand3 root/mnt/sd -t vfat
mount -o loop nand4 root/lnk -t ext2
mount -o loop nand5 root/pw -t ext2

```

This causes the following error:
[COLOR="Red"]
Syntax error: Bad fd number
[/COLOR]

So I have been having users to this:
```

rm /bin/sh
ls -s /bin/bash /bin/sh
./mount.sh

```

One user did this and it worked and he was able to browse the system. But when he went to close the virtual machine it hung up on him. So he tried rebooting and got this:

[COLOR="Red"]
```

init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2450) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2451) terminated with status 255

```
[/COLOR]

He now can't get back into his Virtual Machine. It just hangs there and he can't get to a prompt.

My question is, how can we adjust the mount.sh script so that it will not need the above work-arounds?

---

### Post by geraldm on 2009-02-27
Please edit your script to correct this (if you caught this typo?):
ls -s /bin/bash /bin/sh
ln -s /bin/bash /bin/sh

---

### Post by TCarr on 2009-02-28
The ls or ln was in the documentation. We are trying to eliminate that part of the documentation altogether (ie. not use a symbolic link to /bin/bash at all). We want to alter 'mount.sh' so we don't have to go doing anything with /bin/sh or /bin/bash.

---

### Post by heindsight on 2009-02-28
> **TCarr said:**
> I'm working on a robot development kit for the RoboSapien RS Media. Someone I know wrote a script for it that dumps the firmware and then you can browse it on any linux system by copying the files and mounting them.

Here's the mount.sh we are using:

```

#!/bin/sh

mkdir root >& /dev/null
mkdir root/mnt >& /dev/null
mkdir root/mnt/sd >& /dev/null
mkdir root/mnt/default >& /dev/null
mkdir root/lnk >& /dev/null
mkdir root/pw >& /dev/null

mount -o loop nand1 root -t cramfs
mount -o loop nand2 root/mnt/default -t cramfs
mount -o loop nand3 root/mnt/sd -t vfat
mount -o loop nand4 root/lnk -t ext2
mount -o loop nand5 root/pw -t ext2

```

This causes the following error:
[COLOR="Red"]
Syntax error: Bad fd number
[/COLOR]

Looks like those redirections are wrong. For full details on proper redirection, have a look at the bash manual and the sh manual.
```
man bash
man sh
``` 
I believe that what you wanted was to redirect both stdout and stderr of those mkdir commands to /dev/null. The correct way to do that is:
```
mkdir root > /dev/null 2>&1
```
This will work in both sh and bash

> **TCarr said:**
> 
So I have been having users to this:
```

rm /bin/sh
ls -s /bin/bash /bin/sh
./mount.sh

```


If you want to run a script specifically with bash, the correct way to do that is to put #!/bin/bash at the top.



> **TCarr said:**
> 
One user did this and it worked and he was able to browse the system. But when he went to close the virtual machine it hung up on him. So he tried rebooting and got this:

[COLOR="Red"]
```

init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2450) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2451) terminated with status 255

```
[/COLOR]

He now can't get back into his Virtual Machine. It just hangs there and he can't get to a prompt.

My question is, how can we adjust the mount.sh script so that it will not need the above work-arounds?

On ubuntu, to restore /bin/sh, boot off a live CD, mount the root partition (i'll assume /dev/sda1):
```
sudo mount /dev/sda1 /mnt
```
Then fix the /bin/sh symlink:
```
cd /mnt/bin
sudo ln -s /bin/dash sh
```

---

### Post by TCarr on 2009-02-28
Thank you. You are right about the dash part. I've adjusted mount.sh so that it /bin/bash. One other in the forum (the guy that wrote the script) also said to do this. I tested this on a new VM install of Ubuntu Server and it worked good.

Now we won't need to do any renaming/moving of files.

---

