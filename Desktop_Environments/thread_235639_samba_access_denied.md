---
title: "samba: access denied"
date: 2006-08-13
forum: Desktop Environments
---

### Post by ym4546 on 2006-08-13
i'm trying to set up a samba server to share files.

i'm on kubuntu 6.06...i did not want any authentication, so i followed these instructions from the wiki: 
[https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare?highlight=%28samba%29](https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare?highlight=%28samba%29)

here's what i added to that file: (as per instructions from the wiki)
[hda5]
path = /media/hda5
available = yes
browseable = yes
public = yes
writable = yes
create mask = 0777
hide dot files = No
dos filetime resolution = Yes
guest ok = yes
revalidate = No
browse list = yes

the share shows up in windows, but when i go to browse it, it says access denied, you do not have permissions to access this resource.

do i need to add a force user line or something like that?
i'm wondering if i need to somehow enable the guest user or enable nobody? really not sure.

i'm sort of a linux noob, so the easier to understand your instructions are, the better :)...if you could post exactly what to enter into the terminal, it would be much appreciated.

thanks for your help.

---

### Post by vijirajan on 2006-08-13
Can you tell me what filesystem /media/hda5 contains and its permissions?

---

### Post by foolsh on 2006-08-13
you should 
sudo konqueror
then browse to the folder that is shared and right click the folder then select properties from the list
next click the permissions and change the group: and others: drop down list to read can view & modify content
click ok and exit

---

### Post by ym4546 on 2006-08-13
i have set owner, group, and others to "can view and modify content"...if i understand permissions correctly, that is 0777.

i will now try again....and thanks a lot for the incredibly quick responses.

---

### Post by ym4546 on 2006-08-13
nope not working...i restarted the samba service and tried too: like this:

sudo /etc/init.d/samba restart

---

### Post by foolsh on 2006-08-13
try
sudo fdisk -l /media/hda5

---

### Post by foolsh on 2006-08-13
is this a cdrom drive?

---

### Post by ym4546 on 2006-08-13
that won't format it right??

what is fdisk (not the dos fdisk command i trust?)

---

### Post by foolsh on 2006-08-13
no here is what it output on mine
ben@darkstar:~$ sudo fdisk -l /dev/sda
Password:

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2429    19510911    7  HPFS/NTFS
/dev/sda2            2430        4678    18065092+  83  Linux
/dev/sda3            4679        4863     1486012+  82  Linux swap / Solaris

---

### Post by ym4546 on 2006-08-13
it didn't spit out any thing...just gave me another line...and no this is not a cd-rom drive

---

### Post by foolsh on 2006-08-13
open konquror and type settings:/ in the address bar then browse to internet & network there you should see the samba icon and see if the share is listed in the shares tab

---

### Post by ym4546 on 2006-08-13
it's listed there

---

### Post by foolsh on 2006-08-13
try
sudo fdisk -l /dev/hda5
then

---

### Post by ym4546 on 2006-08-13
yatin@ubuntu:~$ sudo fdisk -l /dev/hda5

Disk /dev/hda5: 13.6 GB, 13686833664 bytes
255 heads, 63 sectors/track, 1663 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

---

### Post by foolsh on 2006-08-13
open the settings:/ address in konqueror again browse to the samba dialog and click the administrator mode button at the bottom
make sure the security level says share on the first screen 
and on the shares tab highlight the share and click edit share at the bottom and make sure readonly is NOT selected

---

### Post by ym4546 on 2006-08-13
done...but still not working

---

### Post by ym4546 on 2006-08-13
sorry...i have to leave just now...will be back soon....thank you very much for your (instantaneous) help..

hope we can fix this.

---

### Post by foolsh on 2006-08-13
try restarting both computers to refreash the samba and windows network services

---

### Post by ym4546 on 2006-08-13
> **foolsh said:**
> try restarting both computers to refreash the samba and windows network services
tried...but still didn't work

---

### Post by Stormbringer on 2006-08-14
> **ym4546 said:**
> i'm trying to set up a samba server to share files.

i'm on kubuntu 6.06...i did not want any authentication, so i followed these instructions from the wiki: 
[https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare?highlight=%28samba%29](https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare?highlight=%28samba%29)

By following that instructions you miss out some important steps  as I'd like to call it "a little tooooooo basic" ... please have a look at the HOWTO I wrote on the matter (see signature below); I'm sure it'll help you to get it going.

If you need help feel free to ask.

---

