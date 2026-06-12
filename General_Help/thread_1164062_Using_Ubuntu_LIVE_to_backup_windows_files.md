---
title: "Using Ubuntu LIVE to backup windows files?"
date: 2009-05-19
forum: General Help
---

### Post by xeroguitar on 2009-05-19
Is this possible? My friend uses Windows Vista. Well as is expected from such Microsoft products, it has gone corrupt and he cannot get Windows to boot up (It gets to a certain point then a blue screen flashes to fast to read and it reboots itself).

He has very important pictures of his daughter from birth up til now (she's 2 years old). He never backed anything up.

I know the files are still there the question is how can I get to them to put them on a CD? I tried using Ubuntu Live CD (8.10) and I got an error saying that it cannot Mount the hard drive... stating I can force it to mount an NTFS drive at my own risk but I have to be under root user... Can I run the LIVE disc as root?

Any other suggestions? 

Thanks!

---

### Post by EXCiD3 on 2009-05-19
If the Windows NTFS partition is fine then you shouldn't have a problem. It's probably asking you because the NTFS partition was not unmounted properly which requires a force mount. 

Create a folder on hte desktop you would like to use as the mount point to access the drive and then run the following command in terminal to mount it. You may need to open up the Partition Editor to find which /dev device the NTFS drive is. (Replace XX with letter and number for the drive and <folder name> with the folder you created)

```
sudo mount -t ntfs-3g /dev/sdXX ~/Desktop/<folder name> -o force
```That should work. You can then plugin a flash drive and copy the pictures and files to there and you should be fine.

Afterwards give them the Ubuntu CD and install it on their PC for them so they don't have trouble like this again. ;)

---

### Post by mjitkop on 2009-05-19
That's a great explanation from EXCiD3! I almost found myself in the same situation once and I wouldn't have known what to do using the Live CD either. This is very good to know. :)

Out of desperation, if nothing worked for me, I would take that hard drive out and put it in a working computer as a slave drive and copy the files there. ;)

---

### Post by EXCiD3 on 2009-05-19
> **mjitkop said:**
> That's a great explanation from EXCiD3! I almost found myself in the same situation once and I wouldn't have known what to do using the Live CD either. This is very good to know. :)


No problem. Just glad to be of some help to at least someone here. ;)

> Out of desperation, if nothing worked for me, I would take that hard drive out and put it in a working computer as a slave drive and copy the files there. ;)

That would work as well. Not quite as easy to do but certainly gets the job done. Hope you can get everything backed up safely! As a side note, once you do get the backed up, why don't you upload them all to an online storage service. Dropbox (file sync to online storage and other computers) and Flickr are two good services that I would recommend strongly. If anything happens to your local copies you can just hop online and grab backups.

---

### Post by xeroguitar on 2009-05-20
> **EXCiD3 said:**
> If the Windows NTFS partition is fine then you shouldn't have a problem. It's probably asking you because the NTFS partition was not unmounted properly which requires a force mount. 

Create a folder on hte desktop you would like to use as the mount point to access the drive and then run the following command in terminal to mount it. You may need to open up the Partition Editor to find which /dev device the NTFS drive is. (Replace XX with letter and number for the drive and <folder name> with the folder you created)

```
sudo mount -t ntfs-3g /dev/sdXX ~/Desktop/<folder name> -o force
```That should work. You can then plugin a flash drive and copy the pictures and files to there and you should be fine.

Afterwards give them the Ubuntu CD and install it on their PC for them so they don't have trouble like this again. ;)

thanks! i will try this tonight... i did manage to talk him into letting me install ubuntu when im done ;-) hopefully he likes it enough to keep it then

---

### Post by MichaelDance on 2009-05-20
> **xeroguitar said:**
> Is this possible? My friend uses Windows Vista. Well as is expected from such Microsoft products, it has gone corrupt and he cannot get Windows to boot up (It gets to a certain point then a blue screen flashes to fast to read and it reboots itself).
 
He has very important pictures of his daughter from birth up til now (she's 2 years old). He never backed anything up.
 
I know the files are still there the question is how can I get to them to put them on a CD? I tried using Ubuntu Live CD (8.10) and I got an error saying that it cannot Mount the hard drive... stating I can force it to mount an NTFS drive at my own risk but I have to be under root user... Can I run the LIVE disc as root?
 
Any other suggestions? 
 
Thanks!
 
The Blue screen - Blue Screen of Death
When you start Windows, your computer may briefly display the blue startup screen and then continuously restart. 
 

This behavior can occur if the following conditions exist: 
[LIST]
[*]A fatal system error (STOP error) causes the computer to stop.
[*]The **Automatically Reboot** option is enabled under **Recovery** on the **Startup/Shutdown** tab in the **System** properties.
 
**Note**: In Windows Server 2000, the **Automatically Reboot** option is enabled in the **Startup and Recovery** dialog box. This dialog box appears after you click the **Startup and Recovery **button on the **Advanced** tab in the **System** properties.
[*]The Windows paging file is smaller than the amount of physical memory installed in the computer or there is insufficient free space on the system hard disk to write the error dump file (Memory.dmp).
[/LIST]**Important** This section, method, or task contains steps that tell you how to modify the registry. However, serious problems might occur if you modify the registry incorrectly. Therefore, make sure that you follow these steps carefully. For added protection, back up the registry before you modify it. Then, you can restore the registry if a problem occurs. For more information about how to back up and restore the registry, click the following article number to view the article in the Microsoft Knowledge Base: 
[322756]("http://support.microsoft.com/kb/322756/") ([http://support.microsoft.com/kb/322756/](http://support.microsoft.com/kb/322756/) ) How to back up and restore the registry in Windows
 
**NOTE**: To work around this issue, you require a parallel installation of Windows.
 

To make the necessary changes, follow these steps: [LIST=1]
[*]Install Windows to a different folder.
[*]Run Regedt32.exe from the new installation of Windows, and then go to the **HKEY_LOCAL_MACHINE** key.
[*]On the **Registry** menu, click **Load Hive**, and then open the System file in the original Windows installation location. By default, this installation is located at %SystemRoot%\System32\Config\System.
[*]Enter an arbitrary name when you receive a prompt for a key name in the **Load Hive** window. This loads the original HKEY_LOCAL_MACHINE hive as a subkey of the current key.
[*]Change the value data in the AutoReboot value to 0 (zero), instead of 1, in the following key: **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl**
[*]Collapse the HKEY_LOCAL_MACHINE subkey and unload the hive.
[/LIST]This disables the Automatically Reboot option in the original Windows installation. After you follow these steps, you may be able to gather information from the STOP error message and resolve the problem that prevents the computer from starting. 
 
Another workaround may be necessary if the minimum size of the paging file is set to a value less than the amount of physical memory. Windows requires a paging file on the system drive large enough to hold all of physical memory, plus 1 megabyte (MB), to write debugging information. You can modify the PagingFiles value of the original installation so that the dump file can be created by the STOP error message. Enough free disk space must be available on the system drive for the paging file. 
 

Follow these steps to change the PagingFiles value in the System file in the original Windows installation location: [LIST=1]
[*]Follow steps 1-4 from the preceding workaround.
[*]Change the data value of the PagingFiles value to allow a minimum value of the amount of physical memory plus 1 MB, but not greater than the amount of free space on the hard disk. The key name is: **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Memory Management**
For example: "drive:\pagefile.sys nnnnnn" where drive is the letter of the system hard disk and nnn is a number for the minimum and maximum size of the paging file.
[*]Check the following key to verify that the CrashDumpEnabled value is set to a data value of 1: **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl**
[*]Collapse the **HKEY_LOCAL_MACHINE** subkey and unload the hive.
[*]Attempt to start the original installation of Windows and the STOP error message should appear. The dump information is stored in the paging file.
[*]Restart the computer and select the parallel installation of Windows. This allows the dump file to be created and you may be able to use the information to resolve the problem that causes the STOP error message in the original installation. 
 
**NOTE**: The dump file is saved in the %SystemRoot%\Memory.dmp file, where %SystemRoot% is the parallel installation system folder.
[/LIST]Information from Windows [http://support.microsoft.com/kb/174630](http://support.microsoft.com/kb/174630)

---

