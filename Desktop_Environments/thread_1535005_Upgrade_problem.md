---
title: "Upgrade problem"
date: 2010-07-20
forum: Desktop Environments
---

### Post by lataak on 2010-07-20
I just upgraded from Ubuntu 9.1 to Lucid Lynx. After the upgrade, my computer starts properly till login screen. After login, it just show the cursor only and nothing else. There is no icon, or menu, or anything. The cursor is there, the background image is there.

I tried to boot using fail-safe Gnome but it remained the same. It looks to work properly in command line. It also logs in in xterm which I don't understand what it is. That is where I am posting from. I tried to recover but it reports Ubuntu store websites are not reachable though the net is working. What do you advice me? What should I do?

My system is Toshiba laptop A205 series. 
Thanks in advance for ur response.

---

### Post by David Haas on 2010-07-20
You may know that upgrades are much less reliable than clean installs, especially when not all the files in the version to be upgraded have themselves been upgraded. So, if others can't tell you how to fix your problem, you should do a clean install of 10.04.

---

### Post by lataak on 2010-07-21
I know that clean install is better but I loose all the programs I have installed previously and start from nil. Besides the data I have on the computer gets erased on clean install which I don't want. I can't take a back up of all the data - it is too much. 

Anyway, if I couldn't fix the problem, clean install will be my only option. Thanks for your response.

---

### Post by varunendra on 2010-07-22
**While booting, press and hold shift key**. This will bring up the grub boot menu. **Select the older kernel to boot** and see if it lets you log in properly.

But beyond this, I haven't heard of any method to safely roll back to earlier version removing newer one. Although in certain cases, it can be done via synaptic, but it may be difficult & may cause problems.

If booting into earlier kernel seems working fine, then I guess the best you can do is to **create an AptOnCD disc **(with metapackage) to backup your programs (only deb packages you installed via apt-get or synaptic), then do a clean install of Lucid and try adding the AptOnCD disc as an offline repository.

It is always a good method for migrating individual or whole set of programs (choosing metapackage) from one installation to another (although it is meant for migrating between similar versions, but you'd have to reinstall unsupported packages anyway!)

**For saving your data**, defining a separate partition as /home while installing is the best practice (OS is installed on /, and user-data is kept on /home). If your current partition plan is not like that, then backing up on an external drive is the recommended option. If you don't have an external media large enough to hold all your data, you can use gparted to resize/move your current partitions (it is risky though!) then create a new one to install Lucid upon.

Feel free to ask if you need detailed instructions about how to do these :).

---

### Post by lataak on 2010-07-22
The system does not start with old kernel too. After booting to the empty window, when I try to shutdown the system using Ctr+Alt+Del, it says that A program is running/unresponsive. It displays the message in small window saying "You will lose ur data if u shutdown...". File manager is the program reported as still running. Do you think the problem lies on the File manager program (I am not sure about this program)?

On my computer, I have three partitions: one ext4 partition, one ext3 partition(where the crashed Ubuntu is installed), and one NTFS (I used to run Vista) partition. I could move the data to other partitions and install clean. However, since the OS has failed, there is no way to move the data to other partitions.

Thanks very much varunendra.

---

### Post by varunendra on 2010-07-22
> **lataak said:**
> I could move the data to other partitions and install clean. However, since the OS has failed, there is no way to move the data to other partitions.

No need for thanks :).
For a clean install, you'll need to boot from a cd or a USB drive anyway. Use LiveCD or Live USB to boot into a live session from where you can move the data.

If there are some important .deb packages you installed via synaptic or apt-get, they should still be there in /var/cache/apt/archives in the ext3 partition. You can simply copy them from there to reinstall later without downloading them again (however, you must install their dependencies manually if required).

I have no idea about the file-manager program.

---

### Post by lataak on 2010-07-22
I will try that in the next two three days and come back with the result.

---

### Post by WinRiddance on 2010-07-22
> **lataak said:**
> I know that clean install is better but I loose all the programs I have installed previously and start from nil. Besides the data I have on the computer gets erased on clean install which I don't want. I can't take a back up of all the data - it is too much. 

Anyway, if I couldn't fix the problem, clean install will be my only option. Thanks for your response.

I know it's too late for that right now - unless you're willing to become involved with Gparted - but the optimum way to install Ubuntu or most other Operating Systems for that matter, is by keeping the Operating System all by itself in a partition, while creating another larger partition for all personal data.

Your /home/user/documents and other folders such as pictures, music, videos, can easily be copied quickly to that second partition and you can make instantly accessible shortcuts to the new locations in your file manager. That way you'll always be able to make a clean installation without losing any important, personal data.

With Gparted (can be used directly from the LiveCD) you can still do that. Boot into Ubuntu as though you were just trying it out via the LiveCD. Then open Gparted - unmount your disk if mounted - resize it, making it smaller with new empty space on the right - format the newly created empty space as a new ext3 or ext4 partition - then copy personal files as described above to the new partition. Once that's done, you can do a clean install of Ubuntu on the same partition where it is right now .... :D

---

### Post by lataak on 2010-07-23
> **WinRiddance said:**
> I know it's too late for that right now - unless you're willing to become involved with Gparted - but the optimum way to install Ubuntu or most other Operating Systems for that matter, is by keeping the Operating System all by itself in a partition, while creating another larger partition for all personal data.
Not too late! I can still do that because I have a free ext4 partition on my system. I don't have to use Gparted right now(I have used Gparted live to create those partitions previously).

> **WinRiddance said:**
> Your /home/user/documents and other folders such as pictures, music, videos, can easily be copied quickly to that second partition and you can make instantly accessible shortcuts to the new locations in your file manager. That way you'll always be able to make a clean installation without losing any important, personal data.
That is a very good point. Keeping the OS and the data on different partitions make the system more flexible and easier to manage. The data will be safer also. I will practice this in the future.

---

