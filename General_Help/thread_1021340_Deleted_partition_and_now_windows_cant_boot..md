---
title: "Deleted partition and now windows cant boot."
date: 2008-12-25
forum: General Help
---

### Post by grand_tale on 2008-12-25
hey guys. im very desperate here i hope you can help. 

im new to linux and stuff and i think i did something wrong. now i cant even load windows. here is what i did..

1. i installed ubuntu on a seperate partition. 
2. i went into windows and deleted the partition because i got some error   when i wanted to enter commands in the terminal window. i copied a command line that i found on the forum to update media players or something.

3. when i restarted my laptop i got an error saying "GRUB  Loading stage1.5      GRUB Loading, please wait... Error 15"


4. then..i tried installing ubuntu again just so i could use my laptop in some way but the installation didnt complete. gave me an error saying it couldnt install apts or something. 

so now the only way i can do anything with my laptop is with the live cd. i really want to get my windows back. i had a bad feeling from the start. i did not delete any other partitions or anything.windows is still there..somewhere.

how can i recover my system?i want it back as it was. my friend said something about resetting my boot.exe or something. but i cant access windows. please guys is there something i can do to get my system back? next time ill read all the tricks of linux before i install things i dont understand.

i have an Acer Aspire 4520 laptop with windows vista.

thanks guys. looking forward to your replies.

have a good day. and merry xmas.

---

### Post by taurus on 2008-12-25
Do you have windows CD?  You can boot your machine from it and fix the MBR.

Otherwise, you can use this, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) to recovery MBR.

---

### Post by caljohnsmith on 2008-12-25
Since you said you have your Live CD handy, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
That will install a Windows equivalent MBR to your sda drive so that you should be able to boot directly into Windows again. How about giving that a shot and let me know how it goes.

---

### Post by grand_tale on 2008-12-25
okay first of all i have to thank you for your advice guys. i used the command codes john gave me in terminal and it worked. but...

windows suggested i do a recovery check so that it could fix any problems. so i did it. but now windows gave me a message and said its unable to repair the problem. i dont have a backup of my windows so i cant use the restore option. is this the end now?

---

### Post by caljohnsmith on 2008-12-25
Do you have a Microsoft Windows Vista Install CD or an OEM Windows Vista Install CD? If you have a Microsoft one, then how about booting it, going to the command line and run:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then run:
```
bootrec /rebuildbcd
```
Reboot, and let me know exactly what happens when you try and boot Vista again.

---

### Post by grand_tale on 2008-12-25
okay...
i switched my laptop off and now all of a sudden i am able to log in. i know im supposed to be happy but im not sure its fixed?or is it maybe how windows works?have errors and then dissapear? i tried to go into cmd from the run option and typed in the commands you gave me coz if there are any errors i want it fixed.this is exactly what my cmd window looks like now. 

"c:\Users\Stian> cd\
 
 c:\> chkdsk /r
 Access denied as you do not have sufficient privileges.
 You have to invoke this utility running in elevated mode.
"
i would like to check it anyway, is this where im supposed to type the commands in ? in cmd?
 
other wise...
if you think its fixed, can i delete my partitions now in the disk management and everything will be okay?

id like to use linux on my laptop but seems like i dont know enough. the documents i read said it was easy but obviously i have a way of messing it up, any documents for idiots you know of?especially the commands stuff.

---

### Post by caljohnsmith on 2008-12-25
> **grand_tale said:**
> okay...
i switched my laptop off and now all of a sudden i am able to log in. i know im supposed to be happy but im not sure its fixed?or is it maybe how windows works?have errors and then dissapear? i tried to go into cmd from the run option and typed in the commands you gave me coz if there are any errors i want it fixed.this is exactly what my cmd window looks like now. 

"c:\Users\Stian> cd\
 
 c:\> chkdsk /r
 Access denied as you do not have sufficient privileges.
 You have to invoke this utility running in elevated mode.
"
i would like to check it anyway, is this where im supposed to type the commands in ? in cmd?
 
other wise...
if you think its fixed, can i delete my partitions now in the disk management and everything will be okay?

id like to use linux on my laptop but seems like i dont know enough. the documents i read said it was easy but obviously i have a way of messing it up, any documents for idiots you know of?especially the commands stuff.
It is best if you run those commands from your Windows Install CD; you can do "chkdsk /r" from a "cmd" window in Vista, and it will schedule to run that command next time you reboot I think. But since you are using Vista, when you open up "cmd", you have to press "Ctrl-Shift-Enter" first to give yourself admin privileges if I remember correctly. I would try booting in and out of Vista at least two or three times just to make sure Vista really is OK now, and if you can, you don't need to worry about running those commands, although they should not hurt, only help. And yes, it should be OK to use Vista's disk management to delete those partitions if you want. If you want to give Linux another shot though, I would leave the partitions, and then try installing Ubuntu using this guide to help you:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

That leads you through the steps fairly well I think. Good luck, let me know how it goes, or if you have more questions.

---

### Post by solwic on 2008-12-25
> **caljohnsmith said:**
> It is best if you run those commands from your Windows Install CD; you can do "chkdsk /r" from a "cmd" window in Vista, and it will schedule to run that command next time you reboot I think. But since you are using Vista, when you open up "cmd", you have to press "Ctrl-Shift-Enter" first to give yourself admin privileges if I remember correctly. I would try booting in and out of Vista at least two or three times just to make sure Vista really is OK now, and if you can, you don't need to worry about running those commands, although they should not hurt, only help. And yes, it should be OK to use Vista's disk management to delete those partitions if you want. If you want to give Linux another shot though, I would leave the partitions, and then try installing Ubuntu using this guide to help you:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

That leads you through the steps fairly well I think. Good luck, let me know how it goes, or if you have more questions.

Could always download Wubi ([www.wubi-installer.org](www.wubi-installer.org)), too.  It's not like having real Ubuntu, but it beats the **** out of Windows Piss-ta.  :P

---

### Post by TeXtonyx on 2008-12-25
Your laptop came with a real Vista install cd, or a Recovery cd
from the manufacturer, or there is a hidden partition on the hard
drive that will restore Vista and all your drivers, but, wipe
out all your data and all but the basic Vista applications. You
should be safe, but look for the recovery cd or read your manual
for how to boot into the hidden recovery partition.

So I think it is time to backup up your important files.

Delete the Ubuntu and swap partitions with Vista. Leave the space
unallocated. Now boot up with the Ubuntu live cd, and choose
install to largest continuous free space (guided). This then
will not touch Vista, even indirectly. 

At Step 7, Advanced, from the drop down menu, choose to install
grub to the /boot partition, which is *not* the default of hd0.
This keeps Vista independent and in control of the booting.

When you reboot you won't get to Ubuntu yet. Download Easybcd,
a free GUI to add OS's to the Vista bootloader menu. Under Linux
add your Ubuntu partition, not swap. If you make a mistake and
add swap it won't hurt, but it won't work. Choose the other
option under Linux then and it will put Ubuntu on your boot menu.

Later, if you uninstall Ubuntu or it gets damaged it won't affect
your Vista operation. If Vista develops a problem, you can boot
to Ubuntu for email and web support. Download free Super Grub Disk
now, which lets you boot Ubuntu separately from Vista if needed.

I think this is the best approach for people who still depend
upon Windows, and are still developing their Linux (grub) skills. 
Easybcd is fast and easy to learn. Dual booting provides a backup
for your internet access. You can get free programs that do much
the same thing as the Windows programs that cost $$$. You could
try the Firefox browser which many people like better than IE.

---

