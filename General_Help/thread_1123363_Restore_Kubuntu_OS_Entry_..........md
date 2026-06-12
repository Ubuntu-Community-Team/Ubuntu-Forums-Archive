---
title: "Restore Kubuntu OS Entry ........."
date: 2009-04-12
forum: General Help
---

### Post by eruptionjoojo on 2009-04-12
Hello everyone,


            I had installed Kubuntu(8.10-32 bit version) in Windows Vista via WUBI installer from the live CD which i have ....


But then i wanted to change the Default OS option to kubuntu from Windows Vista so i downloaded a software known as easy BCD 1.7.2(got the refrence from another thread) ............ while making the appropriate setting via using the software in windows i mistakenly (i guess) removed the Kubuntu entry and rebooted .......


now i can't login into Kubuntu anymore ......... as the only OS listed at the time of booting is Windows Vista ...... i tried using the software(easyBCD) to restore the option but no use .....


now i want your help in creating the Kubuntu entry .........

any help would be greatly appreciated .........
thnxx in advance .......

---

### Post by eruptionjoojo on 2009-04-12
Someone Please guide me as to how to do it ............

---

### Post by eruptionjoojo on 2009-04-13
I really need my Kubuntu back ................

---

### Post by eruptionjoojo on 2009-04-13
Please ......... please ...........
somebody please help me ..........

---

### Post by eruptionjoojo on 2009-04-13
Bump ............ sorry i'm forced:lolflag: to Use the Bump Feature as i'm really in need ............
BUMP ...............

---

### Post by eruptionjoojo on 2009-04-13
BUMP ............... BUMP ................


Bump .............. Bump ..............

---

### Post by eruptionjoojo on 2009-04-13
Bump ............... Bump .........

---

### Post by eruptionjoojo on 2009-04-14
Thank GOD finally i got this problem solved ..................

though i searched a lot to find a solution to this problem of mine .............. but then was left helpless ..................

Since I had installed Kubuntu via Wubi I was almost sure that the Boot MBR being used is Vista's ............. so i needed to create a new entry in windows Vista MBR as Kubuntu and set the Operating System path and drive ........... but then i wasn't sure about the Kubuntu Operating System's path .......... in order to resolve this issue i created a new (Boot entry) kubuntu entry using EasyBCD 1.7.2
{the EasyBCD 1.7.2 utility can be downloaded via the following link :-

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) ............and the Steps needed for making a new enrty using EasyBCD are as follows :-

When you start up EasyBCD, go to Add/Remove entries and click on the Linux tab. Then, you can name the Linux startup option whatever you like. You'll also see a dropdown box that says "Wubi." Don't change this. Now, you will also see another dropdown box that says "Drive." Choose the partition that you installed the Wubi bootloader on. Then, just add entry, and you should be set.}

but since Kubuntu was installed somewhere in C:\(the very same drive as to where Vista was installed) thus i gave the drive path as C:\ to the new entry ...........

then the steps followed for the determination of the exact drive path of the Operating System(Kubuntu) are as follows:-
(1)made a new partition for installing Windows XP on it .
(2).Installed windows XP on the new partition and After the installation was complete tried installing Kubuntu again using the Wubi installer in order to find the correct path of the Operating System(Kubuntu) ...........
(3).after the installation I could clearly see that the path of the Operating System(Kubuntu) was listed as follows:-
{In order to determine the drive path of Kubuntu in Windows XP the Following must be typed in the command prompt :-

C:\windows\system32>bootcfg

(this command would list the Windows XP MBR's Entries which includes the Kubuntu enrty and also the Exact drive path which would be C:\wubildr.mbr)}

C:\Wubildr.mbr

NOTE : thus i needed to make the change in VIsta's MBR and change the Kubuntu Operating System path from C:\ to C:\Wubildr.mbr ..............
(4).now i rebooted via the Windows Vista DVD and recovered Windows Vista MBR ........
(5)then after i changed the boot record manually via command line by setting the Kubuntu entry's Operating System Path to C:\Wubildr.mbr ............

this can be done by using the bcdedit command in Windows Vista Command Prompt and typing the following into the command prompt(but you need administrative privileges for performing these action):-


C:\windows\System32>bcdedit
(this command would show you the current entries listed in the windows Vista's MBR along with their specific identifier's,Operating System path etc. ......... now note down the specific identifier of the Kubuntu enrty )
let's say the specific identifier of the Kubuntu entry is {88b266fo-7d49-ndc-89d2-d25c6946223c}


C:\Windows\system32>bcdedit /set {specific identifier of the Kubuntu entry} path \wubildr.mbr

in the above mentioned case( specific identifier of the Kubuntu entry is {88b266fo-7d49-ndc-89d2-d25c6946223c}) the command would be as follows:-

C:\Windows\system32>bcdedit /set {88b266fo-7d49-ndc-89d2-d25c6946223c} path \wubildr.mbr
The operation completed successfully (this message would be displayed if the made changes were successful)

This command would set the Os path of the Kubuntu enrty to \wubildr.mbr ........... thus loading the Wubi's Mbr ...........

---

