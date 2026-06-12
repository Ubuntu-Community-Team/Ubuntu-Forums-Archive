---
title: "Folder unable to read by Windows7"
date: 2010-04-12
forum: Desktop Environments
---

### Post by richardkwong on 2010-04-12
**<Program Files> Folder unable to read by Windows7** 
This is the 1st time I boot the CD (with Ubuntu 9.10 ISO image) on my HP Notebook (Model CD4510s) (Dual Core T4400 2.2Ghz , 2GB RAM, 320G HardDisc, 16.3 inch 1360x760 display)
running Windows7 Home Premium (32bit).
 
I have not installed the Ubuntu 9.10 yet but it can boot up and run using the Notebook's internal RAM memory.
 
I can use the Ubuntu Firefox to surf the internet under this condition.
 
I can also view the HardDisk 's Windows7 files and file folder.
 
However, I just accidentially DRAG the HardDisk C: drive <Program files> foler onto another directory <C:\temp\). 
 
After I remove the Ubuntu CD and reboot my Notebook.
 
Windows7 boot up normally, but I cannot run any windows program (eg. Internet Explorer:cool: installed under this folder.
 
I recognised the <Program Files> folder is not under C:\.
 
I boot up the Ubuntu 9.10 from the CD again without install Ubuntu 9.10.
 
I use the admin->computer to DRAG the <Program Files> folder from Hard Drive C:\temp back to HardDrive C:\ again.
 
Then I shutdown and remove the CD and boot up Windows7 again.
 
Now Windows7 just keep on saying <c:\Program Files folder is corrupted , please run utility CHKDSK>
 
I think Ubuntu 9.10 has modified the Folder's ownership when I DRAG it back and forth . Windows7 cannot read this folder any more since the ownership is changed from Windows7 administrator to Ubuntu.
 
Can anyone provide a solution to me such that I do not require to re-install all my Windows7 programs again ?/
 
thanks and regards !
 
:sad:
-ricky-

---

### Post by halj32 on 2010-04-12
why dont you try running chkdsk??
if you dont know how boot windows.. run "cmd" as admin
type 
chkdsk /r
this will want to run on next boot.. ok (allow) reboot by typing
shutdown -r -t 00   or use the reboot in windows

OK

---

### Post by richardkwong on 2010-04-12
Dear Halj32,
 
I try to run c:\chkdsk/f under the Windows7 cmd window.
 
But Windows7 just reject me with the following error message 
<u do not have sufficient priviledge to run chkdsk ...>
 
However , my user account is already in the category of <administrator>.
 
Now , I have use the following method to fix this problem :
 
x1. Format a USB key with FAT32 format.
x2. Run Ubuntu with the CD.
X3. Under Places->Computer
X4. Move the <Program Files>  to C:\temp\ agin.
x5. Copy all the files under <Program Files> onto the USB.
x6. Remove CD, boot up in Windows 7 again.
x7. Create a folder <Program Files> under C:\
x8. Copy all the files from USB to this folder again.
 
Reboot the Windows7 and everything work fine !
 
-ricky-

---

