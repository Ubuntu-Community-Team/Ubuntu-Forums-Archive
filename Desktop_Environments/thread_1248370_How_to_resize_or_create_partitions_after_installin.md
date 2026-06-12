---
title: "How to resize or create partitions after installing Ubuntu OS"
date: 2009-08-24
forum: Desktop Environments
---

### Post by sethuaug08 on 2009-08-24
Hi Everyone ,

Am new to Ubuntu OS ,and i would like to get used to it since its a good OS as far i have heard..high end security system.

Fine let me come to my issue here,i tried to resize the partition using Partition Editor..

Steps I followed:
1.Entered Ubuntu Desktop CD
2.System->Administration->Partition Editor
3.It showed me list of Partitions First partition says it holds 71 GB which is full of My Hard Drive,remaining has been taken by OS ,or am not sure what that space is.
4.I resized the First partition ext3 and changed to 20 GB and created 2 more primary paritions.
5.It took arround 15 minutes and it completed the process.

Restarted my system.
Checked if i have specified drive which i have created,but it shows as " 29.8 GB Media " and am not able to paste any files or folder to it.
There is an folder called "lost+found" inside the drive which i created ,not sure what is that.Am wondering why its not showing as D Drive or E Drive as in Windows.

What could be a problem can any one help me on this please??

Please help me guys how to paste my files,and if you can give me a clear explanation about Disk Management in Ubuntu that will be absolutely fantastic. Hands off...

Thanks for all your Help in Advance...

Regards,
Sethu

---

### Post by .kkursor on 2009-08-24
> Checked if i have specified drive which i have created,but it shows as " 29.8 GB Media " and am not able to paste any files or folder to it.
You cannot paste the files to disk as you are running your system as a common user (not root) and default permissions (root:root, rwxr-xr-x or 755 in octal form) do not allow common users to write data to this device.
lost+found is a system folder, you shouldn't bother about its presence, leave it.

> Am wondering why its not showing as D Drive or E Drive as in Windows.
The device naming model of UNIX and Windows (which russians call "offtopic" on UNIX forums) is different. In short, in Ubuntu disk devices are called sdXY, where X is a letter which describes disk number (i.e. sdf - 6-th disk device), and Y is a number which shows partition number, i.e. sdf4 - fourth partition on sixth disk device.

> What could be a problem can any one help me on this please??
The problem is that you cannot write to disk device? If so, run "sudo nautilus &" without quotes in command prompt and enter your password. Then make a directory on your disk device and paste all your files there. Don't forget to recursively change permissions to folder: change its owner to your username. Without it you will not be able to write to the folder.
Cheers!

---

