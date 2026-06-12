---
title: "Grub Error"
date: 2009-01-12
forum: General Help
---

### Post by krnekhelesh on 2009-01-12
Hi, I have a dual boot system with ubuntu 8.10 and windows vista installed.

However, when I tried choosing the ubuntu option in the GRUB menu I get the following error message

```
Error 11: Unrecognized device string
Press and key to continue......
```

And I get this error message for all the grub entries except for windows vista.

Please tell me how to solve this problem.

---

### Post by 5BallJuggler on 2009-01-12
> **krnekhelesh said:**
> 

```
Error 11: Unrecognized device string
Press and key to continue......
```

this is the info that i have, for error 11, but error 16 looks like it's closer to your problem

```
# 11 : "File not found"

This error is returned if the specified filename cannot be found, but everything else (like the disk/partition info) is OK.

# 16 : "Device string unrecognizable"

This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.
```

---

### Post by krnekhelesh on 2009-01-12
So how do I solve the problem?

---

### Post by mikewhatever on 2009-01-12
It looks like you need to check the boot line sintax. If you are not sure what to check, boot from the live cd and the menu.lst file from /boot/grub on your Ubuntu partition.

---

### Post by mgol on 2009-01-12
Maybe You use UUIDs but have 'root' line instead of 'uuid'? Post here Your /boot/grub/menu.lst - use LiveCD to get to it, as mikewhatever has written.

---

### Post by krnekhelesh on 2009-01-12
[B]The GUI Way: Using the Alternate/Install CD and Overwriting the Windows bootloader
Boot your computer with the Ubuntu CD
Go through the installation process until you reach "[!!!] Disk Partition"
Select Manual Partition
Mount your appropriate linux partions:
/
/boot
swap
...
DO NOT FORMAT THEM.
Finish the manual partition
Say "Yes" when it asks you to save the changes
It will give you errors saying that "the system couldn't install ....." after that
Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
Jump to "Install Grub ...."
Once it is finished, just restart your computer[/B]

This was the instructions provided in the official ubuntu community link provided below
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I followed everything carefully, and after restarting my whole ubuntu OS is not installed properly. it has messed up even the previous settings I had.

Why do they post incorrect articles in the community?

---

### Post by krnekhelesh on 2009-01-12
I did not format the partitions but reinstalled GRUB....but the ubuntu installer has reinstalled ubuntu also even when I unchecked the format option.

And the installation was not proper. When i start ubuntu, it says unable to find video drivers....ubuntu is running in low graphhics mode and the mouse is disabled.

---

