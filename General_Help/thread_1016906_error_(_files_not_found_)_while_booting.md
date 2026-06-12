---
title: "error ( files not found ) while booting"
date: 2008-12-20
forum: General Help
---

### Post by &#1575;&#1604;&#1600;&#1588;&#1600;&#1576;&#1600;&#1581; on 2008-12-20
hello

while booting the monitor shows me a message [ input not supported ] and the message stays about 20 seconds or more

and after this message some time the monitor terns into black and some time ubuntu  runs normaly

so I need to restart the computer many times to run ubuntu

and today after the screen turnes into black i restarted the computer

and i saw a new error

and it says that some folder are not found
the folders are :
/ubuntu/disks/boot/grub/menu.lst
/ubuntu/install/boot/grub/menu.lst
/menu.lst
/boot/grub/menu.lst
grub/menu.lst

i tryed to solve the problem by running the live cd and try to copy these files but i failed


currently i am using windows because i cant run ubuntu

---

### Post by &#1575;&#1604;&#1600;&#1588;&#1600;&#1576;&#1600;&#1581; on 2008-12-20
no solution ???????

---

### Post by ajgreeny on 2008-12-20
Try the following and report back what is the output from the terminal in your live CD when you run the commands shown:-

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by &#1575;&#1604;&#1600;&#1588;&#1600;&#1576;&#1600;&#1581; on 2008-12-21
> **ajgreeny said:**
> Try the following and report back what is the output from the terminal in your live CD when you run the commands shown:-

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```Finally reboot, and hopefully you will now have a working grub bootloader.

find /boot/grub/stage1
print screen

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97122&stc=1&d=1229854526[/IMG]

and i tried also
find /grub/stage1



and thank you

---

### Post by ajgreeny on 2008-12-21
That seems very strange as it would appear that there is no /boot/grub/ folder on your computer, which should be there if you did a default install.  Try running the live CD, double click the "Computer" icon on the desktop, then in the left hand pane click the disk icons and search for a /boot/grub folder.  If there really isn't one, It may be simplest to just reinstall you ubuntu system.

There is also a supergrub disk, which I have never used, but which I understand will allow you to install grub if it doesn't exist.  Do a search and investigate further.

---

### Post by &#1575;&#1604;&#1600;&#1588;&#1600;&#1576;&#1600;&#1581; on 2008-12-21
> **ajgreeny said:**
> That seems very strange as it would appear that there is no /boot/grub/ folder on your computer, which should be there if you did a default install.  Try running the live CD, double click the "Computer" icon on the desktop, then in the left hand pane click the disk icons and search for a /boot/grub folder.  If there really isn't one, It may be simplest to just reinstall you ubuntu system.

There is also a supergrub disk, which I have never used, but which I understand will allow you to install grub if it doesn't exist.  Do a search and investigate further.

thank you ajgreeny so much for you help

i downloaded a supergrub CD and i will try it now
if didnt solve the problem I will reinstall ubuntu

but how could i make sure that this problem does not happen again

because this is the second time i face this problem

---

### Post by ajgreeny on 2008-12-22
If that attached picture is from the live CD, which I assume it is, you have not mounted any of your hard disks, as far as I can make out from the icons in the left hand pane, though this may just be an artifact of the picture.  Make sure they are mounted by clicking on the icons for the 41.9GB and Ghost disks, and try the search again, but don't bother with the search the way you did it.  Just look in the folders of the mounted disks, /boot/grub is usually the second one listed on the right hand side.

---

### Post by caljohnsmith on 2008-12-22
Based on the directories you showed in your first post, it looks like you have a Wubi install. That means unfortunately the Super Grub Disk can't help you, because the initial booting process is handled by Windows. It might help your problem if you can boot your Windows Install CD, go to the command line and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try booting Ubuntu again and let me know if anything changes.

---

