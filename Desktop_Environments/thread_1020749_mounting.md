---
title: "mounting"
date: 2008-12-24
forum: Desktop Environments
---

### Post by num on 2008-12-24
hello,

i get the following error when connecting the devices to the linux box. i got ntfs-config installed and i have safetly removed the devices from the computer but i dont understand what is going on. please help.

[IMG]http://i41.tinypic.com/2hedqc4.png[/IMG]

---

### Post by s3gfault on 2008-12-24
yup.  should be fine to just do the command they recommend in that error message

```
sudo mount -t ntfs-3g /dev/sdc1 /media/FreeAgentDrive -o force
```
i think it was.  Basically it says it all right in the details there.  last time the jump drive was in use someone just pulled it out instead of unmounting it, i think.

---

### Post by num on 2008-12-24
should there be a space between:

/sdc1 /media/

?

---

### Post by s3gfault on 2008-12-24
> **num said:**
> should there be a space between:

/sdc1 /media/

?

yes, these are two seperate arguments.  /media is the first part of the path to the mount point.

---

### Post by num on 2008-12-24
what about the other drive Dump # 16?

---

### Post by s3gfault on 2008-12-24
IDK, whats the error message for that one?  same?  if its the same then read the error message and do the command in there that it is telling you.

---

### Post by num on 2008-12-24
I get the following error:

```
administrator@server:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/FreeAgentDrive -o force
[sudo] password for administrator: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/FreeAgentDrive: No such file or directory
administrator@server:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/FreeAgentDrive -o force
fuse: failed to access mountpoint /media/FreeAgentDrive: No such file or directory
administrator@server:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/dump # 16 -o force
fuse: failed to access mountpoint /media/dump: No such file or directory
administrator@server:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/Dump#16 -o forcefuse: failed to access mountpoint /media/Dump#16: No such file or directory
administrator@server:~$ 


```

---

### Post by s3gfault on 2008-12-24
ah, it looks like your mount points do not exist.  because you have to manually mount these now, it might be a good time to review the manpage for mount.  Here are the key problems with your commands
1) sudo mount -t ntfs-3g /dev/sdc1 /media/FreeAgentDrive -o force
Let me break this down.  

"sudo" you know what this does, it launches the mount program with root privileges.

"mount" is a console application that takes two positional arguments and several command switches.  Positional arguments are those arguments to a command who meaning is identified by the order they come in.  In your mount command you have "-t ntfs-3g" and "-o force" these are named arguments, they can generally be positioned anywhere after the name of the command.  Your two positional arguments are "/dev/sdc1" and "/media/FreeAgentDrive".  The first position represents the device that you want to mount.  All of the devices connected to the computer are represented by special files in the /dev directory.  we know that your freeagentdrive is mapped to /dev/sdc1 because this was indicated to us in your error message that is screen shot above.  Now, the second positional argument is "/media/FreeAgentDrive" which represents where the files will be available after the mounting.  If the mount operation is successful then you could cd to that dir after mounting and do `ls` and list the files on the device.  The error message you got indicated that the mountpoint does not exist, so you'll want to add it.

```
sudo mkdir /media/FreeAgentDrive
```
i don't know what the permissions need to be on this dir, but 644 is a safe bet.

There are several problems with your second command
2) sudo mount -t ntfs-3g /dev/sdc1 /media/Dump#16 -o force
these are the problems
*) /dev/sdc1 is probably not correct, since this represents the free agent drive
*) /media/Dump#16 doesn't exist
*) # is not a legal character for a filename

Once you get your first one mounted, then revisit Dump 16, and apply your new skills to making the mount work.

---

### Post by Wisp558 on 2008-12-24
The error message in ur first post is from the drive being marked dirty by 'dows.  Go back into Windows, and disconnect the device CLEANLY. That should fix that and you shouldn't have to force a mount.

---

