---
title: "How to programmatically mount /media/OS?"
date: 2009-06-29
forum: Desktop Environments
---

### Post by wei_jiang on 2009-06-29
Hi,

I found /media/OS (the Windows c: drive) is not available until I click on OS in the file manager. I want to mount it in my application programmatically, so my application can access it without clicking on "OS". How to do it?

Any information would be appreciated. Thanks in advance.

---

### Post by cph05a on 2009-06-29
If you just want to run this in a script, you could make a quick bash script to mount this on start up
```

#!/bash/sh
mount -t ntfs /dev/sda1 /mnt/c-drive 

```

just replace /dev/sda1 with whatever your c drive partition is called. Then go to System/Preferences/Startup Applications and add your script.


If you want to do this from another program, you can run terminal commands from a program like this:

C/C++:
```
(void)system("mount -t ntfs /dev/sda1 /mnt/c-drive");
```

Java:
```

Runtime.getRuntime().exec("mount -t ntfs /dev/sda1 /mnt/c-drive");

```


Edit:
This solution works, but the one below is better.

---

### Post by mcduck on 2009-06-29
> **wei_jiang said:**
> Hi,

I found /media/OS (the Windows c: drive) is not available until I click on OS in the file manager. I want to mount it in my application programmatically, so my application can access it without clicking on "OS". How to do it?

Any information would be appreciated. Thanks in advance.

Actually the best solution would be to simply add the partition into /etc/fstab, to mount it at boot time. :)

See this page for more instructions, if you need any: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by wei_jiang on 2009-06-29
Thank you both [cph05a]("http://ubuntuforums.org/member.php?u=742053") and mcduck for your replys. I tried, but with issues:

1. Command "mount" only can be called by root. 

2. I manually typed "sudo mount -t ntfs /dev/OS /mnt/c-drive" and got an error:
  ntfs-3g: Failed to access volume '/dev/OS': No such file or directory

3. /etc/fstab is only writable by root.

My program (a Java program) is called by a regular user. It is difficult to provide root password to underlying "mount" because a) difficult to provide password; b) difficult to get password prompt...

Is there other solutions? How does the file manager do it please?

---

### Post by mcduck on 2009-06-30
> **wei_jiang said:**
> Thank you both [cph05a]("http://ubuntuforums.org/member.php?u=742053") and mcduck for your replys. I tried, but with issues:

1. Command "mount" only can be called by root. 

2. I manually typed "sudo mount -t ntfs /dev/OS /mnt/c-drive" and got an error:
  ntfs-3g: Failed to access volume '/dev/OS': No such file or directory

3. /etc/fstab is only writable by root.

My program (a Java program) is called by a regular user. It is difficult to provide root password to underlying "mount" because a) difficult to provide password; b) difficult to get password prompt...

Is there other solutions? How does the file manager do it please?

1. Use "sudo". [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

2. /dev/OS is  not a correct name for a hard drive. Check what the drive/partition is really called and use that. ("sudo fdisk -l" will list all your drives and partitions and their device names)

3. See 1.

All of these things were already explained in the fstab guide I linked for you.

..and just to make things clear, I didn't suggest using the mount command in your program, but simply configuring your partition to mount automatically so that your program doesn't have to mount it.

---

