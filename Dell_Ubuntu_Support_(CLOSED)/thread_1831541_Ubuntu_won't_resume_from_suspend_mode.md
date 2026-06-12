---
title: "Ubuntu won't resume from suspend mode"
date: 2011-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maximus1285 on 2011-08-23
Hello everybody... I'm new in the magic Ubuntu's world...
I have a Dell XPS... I just installed a dual boot Win 7 / Ubuntu 11.04

Every time that I'm in Ubuntu and the computer goes to hibernation(Suspend).. It won't resume from that state... The only one way I can get it back to life is by making a hard boot....

Any help on this would be greatly appreciated... :)

---

### Post by Toz on 2011-08-23
Welcome to the forums.

What model of Dell XPS do you have?

Can you also post back the contents of **/var/log/pm-suspend.log** and **/var/log/syslog** (please post back the contents of those files in code (#) blocks)?

---

### Post by Maximus1285 on 2011-08-24
My laptop is XPS 15 (L502X)
Processor = Core i7 2630m 2.0 GHZ
Memory = 8 GB 
Graphics = Nvidia GT 540m 2 GB


Attached you will find the information you requested. Tell me if you need anything else... :)


Thanks for the help.... tell me if you need anything else!! 
And thanks again man!!

---

### Post by Toz on 2011-08-25
Open a terminal window, type in the following command, and post back the results?
```
ls /sys/bus/pci/drivers/xhci_hcd/
```

---

### Post by salins on 2011-08-25
i too face the prblem.. mine is also xps 15
the result is
0000:05:00.0  bind  module  new_id  remove_id  uevent  unbind

---

### Post by Toz on 2011-08-25
> **salins said:**
> i too face the prblem.. mine is also xps 15
the result is
0000:05:00.0  bind  module  new_id  remove_id  uevent  unbind

@salins, can you post back the contents of your **/var/log/pm-suspend.log** and **/var/log/syslog** files? Lets have a look in there and see if something pops up.

USB 3 ports can be problematic for suspend. Since you've shown the contents of your /sys/bus/pci/drivers/xhci_hcd/ directory, you can also try the following to see if it helps (warning: this will require some command prompt work - its just easier and quicker that way).

1. Open a terminal window and type in the following:
```
gksudo gedit /etc/pm/sleep.d/20_custom-xhci_hcd
```
...after entering your password to get access to that directory location, an editor window will open.

2. Copy/paste the following code (specific to your computer) into the gedit window:
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".

case "${1}" in
  hibernate|suspend)
    # Unbind xhci_hcd devices
    echo -n "0000:05:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
  ;;
  resume|thaw)
    # Bind xhci_hcd devices
    echo -n "0000:05:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  ;;
esac 
```
...this will unbind the usb 3 devices when entering sleep/hibernate and rebind them on resume.

3. Save the file

4. We need to make the file executable. Enter this at the command prompt in the terminal window:
```
sudo chmod + x /etc/pm/sleep.d/20_custom-xhci_hcd
```

5. Next, we need to also unload the xhci module. In the terminal window, type;
```
gksudo gedit /etc/pm/config.d/usb3-suspend-workaround
```

6. Copy/paste the following:
```
SUSPEND_MODULES="xhci" 
```

7. Save the file.

Now try suspend and see if it works. If not, post back those files from the beginning of this post.

---

### Post by incognus on 2011-08-25
> **Maximus1285 said:**
> Hello everybody... I'm new in the magic Ubuntu's world...
I have a Dell XPS... I just installed a dual boot Win 7 / Ubuntu 11.04

Every time that I'm in Ubuntu and the computer goes to hibernation(Suspend).. It won't resume from that state... The only one way I can get it back to life is by making a hard boot....

Any help on this would be greatly appreciated... :)

There seem to be many threads dedicated to this problem. I have to say that although i am a proud owner of many laptops running ubuntu, I havent encountered this problem myself. But it seems to be a problem with the graphic hardware kicking back on. Have a look at the options for the program pm-suspend which is part of the power management suite in ubuntu.

```
man pm-suspend
```Something like 
```
sudo pm-suspend --quirk-radeon-off
```would ensure that the Radeon GPU is switched off in sleep mode and switched back on when the machine resumes. 

try to run the command with the desired option and see if the machine wakes up.

These commands are then included in scripts which are executed when you suspend or hibernate.
The script /etc/acpi/sleep.sh has the pm-suspend command at the end of the script. Include the command with the option of choosing like in the example above. See if you can wake up successfully from your dream!  :D

Correct me if I was wrong
Tell me if it worked! 
Cheers!

---

### Post by Maximus1285 on 2011-08-28
TOZ, there are the results after running the code you gave me:
0000:04:00.0  bind  module  new_id  remove_id  uevent  unbind


Thanks again!

---

### Post by Maximus1285 on 2011-08-28
INCOGNUS.

My video card is NVidia GT 540M... so I'm not sure... There's some commands for making sure the video card will be turned back on when resuming, but it warns that if the video card doesn't need this command line, it will call lock ups...

So I'm not sure....

---

### Post by Toz on 2011-08-28
> **Maximus1285 said:**
> TOZ, there are the results after running the code you gave me:
0000:04:00.0  bind  module  new_id  remove_id  uevent  unbind


Thanks again!

Try this:

1. Open a terminal window and type in the following:
```
gksudo gedit /etc/pm/sleep.d/20_custom-xhci_hcd
```
...after entering your password to get access to that directory location, an editor window will open.

2. Copy/paste the following code (specific to your computer) into the gedit window:
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".

case "${1}" in
  hibernate|suspend)
    # Unbind xhci_hcd devices
    echo -n "0000:04:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
  ;;
  resume|thaw)
    # Bind xhci_hcd devices
    echo -n "0000:04:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  ;;
esac 
```
...this will unbind the usb 3 devices when entering sleep/hibernate and rebind them on resume.

3. Save the file

4. We need to make the file executable. Enter this at the command prompt in the terminal window:
```
sudo chmod + x /etc/pm/sleep.d/20_custom-xhci_hcd
```

5. Next, we need to also unload the xhci module. In the terminal window, type;
```
gksudo gedit /etc/pm/config.d/usb3-suspend-workaround
```

6. Copy/paste the following:
```
SUSPEND_MODULES="xhci" 
```

7. Save the file.

Now try suspend and see if it works.

---

### Post by Maximus1285 on 2011-08-29
TOZ.

It worked just fine!! Thanks a lot for your help!!

I have another question, if you don't mind.... 
When I go to additional controllers, it detects that the video card driver is not installed. When I installed the one that says: Recommended by Ubuntu.. And restarted my computer...

It said something like my system didn't count with the appropriate hardware for running Unity, and then it starts Ubuntu on the basics... Unity doesn't work... actually nothing works, and if I check the driver, it says: Driver installed but is not being used...

So I have to uninstall that driver so Unity and everything come back on...

Any advice on this would be greatly appreciated...

---

### Post by Toz on 2011-08-30
Glad it worked.

I think you should open another thread for that problem. I don't have any nvidia cards to be able to advise. There are others on this forum who can advise regarding nvidia and unity.

---

### Post by Byb on 2011-11-17
Hi TOZ
I'm so happy to find this, I have the same issue on my laptop with 3 USB, only in suspend/resume process (Hibernate/Thaw is OK).
Unfortunately I have no xhci, only 3 uhci and 1 ehci (strange, this makes 4 USB ?)
```
moi@moi-Amilo-M7405:~$ ls /sys/bus/pci/drivers/*hci_hcd/
/sys/bus/pci/drivers/ehci_hcd/:
0000:00:1d.7  bind  module  new_id  remove_id  uevent  unbind

/sys/bus/pci/drivers/ohci_hcd/:
bind  new_id  remove_id  uevent  unbind

/sys/bus/pci/drivers/uhci_hcd/:
0000:00:1d.0  0000:00:1d.1  0000:00:1d.2  bind  module  new_id  remove_id  uevent  unbind
``````
lspci | grep USB
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
```
I'd like to try your tip but I don't know how to tweak the script so that it won't change hibernate/thaw.
Should I have 2 or 4 different file names to  unbind all the USB?
```
gksudo gedit /etc/pm/sleep.d/2[0|1|2|3]_custom-[e|u]hci_hcd
```
And is the /etc/pm/config.d/usb3-suspend-workaround file can be named whatever if I unload several modules, or one file per module in which order?

Here the full lspci output, don't you think we miss some device manager to see all hardware attachments/dependancies tree like they have in windows "show devices by connections"? This would help to disable unuseful things.
```
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
01:03.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

Thanks for your help

---

### Post by Toz on 2011-11-17
@Byb. I can see from the bug reports and various forums post entries that you have been struggling with this problem for a while. I don't believe this fix will work for you, because this fix is for USB3 ports (which I don't believe your laptop has any of). In reviewing your posts in this forum, I came across a suggestion made here: [http://ubuntuforums.org/showpost.php?p=10464760&postcount=137]("http://ubuntuforums.org/showpost.php?p=10464760&postcount=137") - leading to this code: [http://ubuntuforums.org/showpost.php?p=6105510&postcount=12]("http://ubuntuforums.org/showpost.php?p=6105510&postcount=12"). Have you tried this suggestion?

If you did and it was not successful, can you do the following (from a terminal window):
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
sudo pm-suspend
```
...and after you have recovered your desktop, post back the contents of the **/var/log/pm-suspend.log** file.

EDIT: Note to self: SUSPEND_MODULES

---

### Post by Byb on 2011-11-17
:lolflag: I like your note to self. Another lol to me, I misunderstood USB3 against 3 USB (in the lap time wikipedia learnt me something more ;) . I just found the USB2 ehci is the thing that hosts my 3 usb ports (with the help of a win xp dual boot, shame on me) and I went back here saying to you not to hury to answer and give me some time to do the test... OK, i read it is not the issue.
Right now, I'll reread carefully your post (I'm not so english), do the things and let you know.
Note to self when I'll read me again : according to my tests, resume worked from HardyHeron to Jaunty included, and went broken since Karmic to Oneiric
I come back very soon
Thanks for you kindly be my white stick

---

### Post by Byb on 2011-11-17
TOZ, I'm back. Well I read the link to post #12 and remember I did not tried this as for my single processor pc, disabling all but one proc means do nothing. Nor I have the GM45.
So here is the pm-suspend.log after the lobotomic sudo pm-suspend. I saw in it a strange thing called novatel-3G among other strange (this is a fresh untainted install with only the mainline kernel 3.2rc2 as Tim from Launchpad requiered)
Thanks again and sorry I can't pick a beer for you in the smilies (I've already fed the forum with popcorn)

---

### Post by Toz on 2011-11-17
Hmmm - we didn't get the fully debugged log file. Can you try this instead:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```
...then after recovery post back /var/log/pm-suspend.log. The log file should be much bigger with many more debug statements. Also then post back results of:
```
cat /var/log/syslog* | grep PM:
```

Have you tried the **acpi_sleep=nonvs** kernel parameter?

---

### Post by Byb on 2011-11-18
Hi TOZ
I really appreciate you being there and give some of your time.

> **Toz said:**
> Hmmm - we didn't get the fully debugged log file. Can you try this instead:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```...then after recovery post back /var/log/pm-suspend.log. The log file should be much bigger with many more debug statements. Also then post back results of:
```
cat /var/log/syslog* | grep PM:
```
sudo bash
[sudo] password for moi: 
root@moi-Amilo-M7405:~# mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
root@moi-Amilo-M7405:~# export PM_DEBUG=true
root@moi-Amilo-M7405:~# date
vendredi 18 novembre 2011, 07:45:18 (UTC+0100)

> Have you tried the **acpi_sleep=nonvs** kernel parameter?Yes, I did when I had issue with hibernation too. I learned nonvs means "no non volatile storage" and is intended to prevent suspend to disk (maybe I misunderstood. whatever, hibernation works, the issue was from a change I made in partition and swap uuid changed, breaking hibernation)

Now I pm-supend and come back to edit this post

---

### Post by Byb on 2011-11-18
New post instead.
It seams the pm events from syslog are related to hibernation.
pm log  is more heavy this time

---

### Post by Toz on 2011-11-18
Some more questions:

1. Exactly what happens when you resume? How do you initiate resume? Blank screen? Any flashing LEDs? Are the LEDs on? How do you recover?

2. What is your kernel command line:
```
cat /proc/cmdline
```

3. Have you tried the following lernel parameters:
```

acpi_sleep=s3mode
acpi_sleep=s3bios

```

4. Have you tried s2ram?
```
sudo apt-get install uswsusp
```
Does it work?
```
sudo s2ram
```
...or, if you get an error,
```
s2ram -f
```

5. Is there anything in your BIOS about acpi sleep or sleep state settings?

6. What are the contents of **/etc/initramfs-tools/conf.d/resume** and the results of:
```
sudo blkid
```

---

### Post by Byb on 2011-11-18
Which kernel do you want I diagnose with?
3.0.0-12-generic
or
3.2.0-030200rc2-generic ?

I have these 2 on a fresh install (spare single boot 20GB HDD I can format and reformat as you like):cool:

---

### Post by Toz on 2011-11-18
Lets try with 3.0.0-12-generic.

---

### Post by Byb on 2011-11-18
> **Toz said:**
> Some more questions:
1. Exactly what happens when you resume? How do you initiate resume? Blank screen? Any flashing LEDs? Are the LEDs on? How do you recover?
I resume with the Power button. The PC starts, wifi led goes solid on if the switch is on, the sleep led goes off, a small HHD arm noise+HHD led lits for 1/4s then goes off...then screen remains bla(n|c)k
note to self... i just read a Ctrl+d thing about PC falling in buzybox??? to try.
> 2. What is your kernel command line:
```
cat /proc/cmdline
``````

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=d1565e0c-2dcb-4ebf-8326-0a28127b78f0 ro
```> 3. Have you tried the following lernel parameters:
```

acpi_sleep=s3mode
acpi_sleep=s3bios

```No I did not, I tried all pm-suspend --quirk-xxx options in command line. I'll try like you say
My laptop in the MaxReboot Award Winner
Are these option to be place all at once beside the quietsplash in /etc/default/grub/ ?
> 4. Have you tried s2ram?
```
sudo apt-get install uswsusp
```Does it work?
```
sudo s2ram
```...or, if you get an error,
```
s2ram -f
```Yes I did on the other HDD.
here is the output, I'm afraid the install did not update 3.0.0-12: see that
```
sudo dpkg-query -l 'uswsusp'
[sudo] password for moi: 
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version        Description
+++-==============-==============-============================================
un  uswsusp        <none>         (aucune description n'est disponible)
moi@moi-Amilo-M7405:~$ sudo apt-get install uswsusp
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets supplémentaires suivants seront installés : 
  liblzo2-2
Les NOUVEAUX paquets suivants seront installés :
  liblzo2-2 uswsusp
0 mis à jour, 2 nouvellement installés, 0 à enlever et 14 non mis à jour.
Il est nécessaire de prendre 224 ko dans les archives.
Après cette opération, 811 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? O
Réception de : 1 http://fr.archive.ubuntu.com/ubuntu/ oneiric/main liblzo2-2 i386 2.05-1 [60,8 kB]
Réception de : 2 http://fr.archive.ubuntu.com/ubuntu/ oneiric/universe uswsusp i386 1.0-1ubuntu1 [164 kB]
224 ko réceptionnés en 0s (712 ko/s)
Préconfiguration des paquets...
Sélection du paquet liblzo2-2 précédemment désélectionné.
(Lecture de la base de données... 131412 fichiers et répertoires déjà installés.)
Dépaquetage de liblzo2-2 (à partir de .../liblzo2-2_2.05-1_i386.deb) ...
Sélection du paquet uswsusp précédemment désélectionné.
Dépaquetage de uswsusp (à partir de .../uswsusp_1.0-1ubuntu1_i386.deb) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de liblzo2-2 (2.05-1) ...
Paramétrage de uswsusp (1.0-1ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Traitement des actions différées (« triggers ») pour « libc-bin »...
ldconfig deferred processing now taking place
Traitement des actions différées (« triggers ») pour « initramfs-tools »...
update-initramfs: Generating /boot/initrd.img-3.2.0-030200rc2-generic
uname -a
Linux moi-Amilo-M7405 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```???
I must feel the other answers before I try, you understand why ;) 
> 5. Is there anything in your BIOS about acpi sleep or sleep state settings?I tried the 2 single options I have: power button as ON/OFF or SUSPEND (help says it is for DOS mode)
and the ENABLE/DISABLE the QUIET FAN button
> 6. What are the contents of **/etc/initramfs-tools/conf.d/resume** and the results of:
```
sudo blkid
``````
cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=5f0839d7-7b2f-41d3-a635-927a7861308d
```It is not the same than my /proc/cmdline.... strange?
```
sudo blkid
[sudo] password for moi: 
/dev/sda1: UUID="d1565e0c-2dcb-4ebf-8326-0a28127b78f0" TYPE="ext4" 
/dev/sda5: UUID="5f0839d7-7b2f-41d3-a635-927a7861308d" TYPE="swap"
```

---

### Post by Byb on 2011-11-18
both s2ram and s2ram -f do the same as pm-supend

---

### Post by Byb on 2011-11-18
I added this line on boot, all in the end:
options="acpi_sleep=S3bios acpi_sleep=S3mode"
then ctrl+x

After boot and suspend, pc hangs as usual on resume  :-&

---

### Post by Toz on 2011-11-18
> **Byb said:**
> I added this line on boot, all in the end:
options="acpi_sleep=S3bios acpi_sleep=S3mode"
then ctrl+x

After boot and suspend, pc hangs as usual on resume  :-&

Try them one at a time. First **acpi_sleep=S3bios** then on second try, **acpi_sleep=S3mode**.

From what I've seen so far, you're system isn't even initiating the resume phase (the pm-suspend.log does not have any entries for the resume phase). This leads me to believe it is either a bios or acpi problem. You have checked the bios and there is nothing there. In addition to the above kernel parameters, can you also try the following, one at a time:
**acpi_osi=Linux**
[B]acpi_osi=\"Windows 2006\"
noapic
noacpi[/B]

After each attempt with kernel parameter, have a look at /var/log/pm-suspend.log to see if there is any evidence of the resume scripts running. Look for something like:
> Wed Nov  2 05:42:10 EDT 2011: Awake.
Wed Nov  2 05:42:10 EDT 2011: Running hooks for resume
If you find them, post back a copy of the file along with which kernel parameter did that. (And of course, if resume worked).

If none of those kernel parameters work, we will have to dig deeper. There are other debugging options.

---

### Post by Byb on 2011-11-19
Thank you for being firm TOZ.
I also said there seem to be a short HDD access on resume, so it could be a problem resuming the HDD, preventing anything to be logged: stupid idea?
Whatever, I'll try the tests you advise.

---

### Post by Toz on 2011-11-19
> **Byb said:**
> I also said there seem to be a short HDD access on resume, so it could be a problem resuming the HDD, preventing anything to be logged: stupid idea?
It could just be the power surge when the computer resumes in re-initiating the drive. Is anything being logged in /var/log/syslog at this point in time?

---

### Post by Byb on 2011-11-20
Hi TOZ
There don't seem anything loged between the time I request suspend and the time I hard-reboot after the hang.
Immediatly on resume, (just before hang) the wifi led turns on, suspend (moon) led stops blinking to OFF state and HDD led briefly lights ~1/2s. Then this HDD led goes back off for a "long" 1/2~3/4s and goes ON again for the about same time before it definitively goes OFF.
I join a syslog part showing the suspend request on 20h26 and the hard-restart on 20h37.

 						I read your previous post with big interrest, particularly the **acpi_osi=\"Windows 2006\" ** thing because the suspend/resume works OK in Windows. I think this is the next thing I will try after this one I found in the packet uswsusp you advised:
First I found my system is not really in the database:
```
sudo s2ram -n
[sudo] password for moi: 
ATTENTION:
Your machine is in the whitelist  but the entry has not been confirmed.
You may try to find better options than previously reported.

Machine matched entry 338:
    sys_vendor   = 'FUJITSU SIEMENS'
    sys_product  = 'Amilo M*'
    sys_version  = ''
    bios_version = ''
Fixes: 0x2c  VBE_SAVE VBE_POST UNSURE 
This machine can be identified by:
    sys_vendor   = "FUJITSU SIEMENS"
    sys_product  = "Amilo M7405 "
    sys_version  = "                      "
    bios_version = "1.03C  "
```

Then I learnt a tip in the package doc REAME.s2ram-whitelist.gz that says to try in a very light environment init=/bin/bash . Don't know how to do that, but I will try

---

### Post by Toz on 2011-11-20
If your system isn't being recognized by s2ram, then you can force it via:
```
sudo s2ram -f
```
...and based on the response from the previous s2ram, I would also try:
```
sudo s2ram -f -p -s
```

To boot in an limited environment, add **init=/bin/bash** to the kernel command line during boot. Instructions are here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

---

### Post by Byb on 2011-11-21
> **Toz said:**
> If your system isn't being recognized by s2ram, then you can force it via:
```
sudo s2ram -f
```...and based on the response from the previous s2ram, I would also try:
```
sudo s2ram -f -p -s
```To boot in an limited environment, add **init=/bin/bash** to the kernel command line during boot. Instructions are here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot).
Thank you TOZ, I even found how to boot in the minimal init=/bin/bash mode, appending 1 after the line /boot ....ending with ro (I removed quietsplash from it in my grub2).
After the 1 I added one by one your 4 tips acpi_osi=Linux \"Windows 2006\" noapic noacpi and also nolapic Winows 2001 and windows 2001 SP2 and apm. BTW in the link above acpi_osi=linux is with no capitalized L for Linux... important ?
Only booting in /bin/bash (kernel option 1) I tried the 10 s2ram -f combinations ( -a -m -s -p) found in the s2ram-whitelist doc and the same 10 with the -v parameter : all failed :( , on resume nor the CapsLock nor the NumLock keys lit the corresponding LEDs, and always black screen.
I also discovered that the HDD arm noise on resume I spoke about before was not a hdd noise, but a CDROM reader noise. Now I leave the try opened (my bios boot sequence is set HDD-none-none-none).
During the tests with s2ram in single user mode there was errors when I mount /proc and /sys (~ already mounted~) :confused: (maybe uswsusp is not compatible with 3.0.0-12 ? )
BTW, did you see the last remount ext4 thing in my log just in the end of the suspend request?

I found in a doc [acpi_guideline_for_vendors.pdf]("ftp://ftp.suse.com/pub/people/trenn/ACPI_BIOS_on_Linux_guide/acpi_guideline_for_vendors.pdf") info about a CD that tests the bios compatibility. I will try to try this now

---

### Post by Byb on 2011-11-21
> **Toz said:**
> If your system isn't being recognized by s2ram, then you can force it via:
```
sudo s2ram -f
```...and based on the response from the previous s2ram, I would also try:
```
sudo s2ram -f -p -s
```To boot in an limited environment, add **init=/bin/bash** to the kernel command line during boot. Instructions are here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot).
Thank you TOZ, I even found how to boot in the minimal init=/bin/bash mode, appending 1 after the line /boot ....ending with ro (I removed quietsplash from it in my grub2).
After the 1 I added one by one your 4 tips acpi_osi=Linux \"Windows 2006\" noapic noacpi and also nolapic Winows 2001 and windows 2001 SP2 and apm. BTW in the link above acpi_osi=linux is with no capitalized L for Linux... important ?
Only booting in /bin/bash (kernel option 1) I tried the 10 s2ram -f combinations ( -a -m -s -p) found in the s2ram-whitelist doc and the same 10 with the -v parameter : all failed :( , on resume nor the CapsLock nor the NumLock keys lit the corresponding LEDs, and always black screen.
I also discovered that the HDD arm noise on resume I spoke about before was not a hdd noise, but a CDROM reader noise. Now I leave the try opened (my bios boot sequence is set HDD-none-none-none).
During the tests with s2ram in single user mode there was errors when I mount /proc and /sys (~ already mounted~) :confused: (maybe uswsusp is not compatible with 3.0.0-12 ? )
BTW, did you see the last remount ext4 thing in my log just in the end of the suspend request?

I found in a doc [acpi_guideline_for_vendors.pdf]("ftp://ftp.suse.com/pub/people/trenn/ACPI_BIOS_on_Linux_guide/acpi_guideline_for_vendors.pdf") info about a CD that tests the bios compatibility. I will try to try this now

---

### Post by Byb on 2011-11-21
all 4 vanilla fc6 mandriva2007.1 & ubuntu7.04 manual suspend/resume tests from CD failed on resume
Now I'm burning a 7.04 LiveCD to see if it works fine like Jaunty and Windows XP up to SP3 did.

---

### Post by Byb on 2011-11-21
A fresh install of 9.04Jaunty works out of the box with NO parameters passed to the kernel- please see attachment. (resume hanged from liveCD session. After, I performed the installation directly, without going via the "test without changing your hdd" option) 
 
7.04 liveCD did not have suspend option. I did not installed it.

---

### Post by Byb on 2011-11-21
Do I see the tunnel exit? I tried my Oneiric test installation with the quirks I found in the Jaunty pm-suspend.log .... and it worked :):):):)
```
sudo pm-suspend --quirk-dpms-suspend --quirk-dpms-on --quirk-vbestate-restore --quirk-vbemode-restore --quirk-vga-mode3 --quirk-vbe-post
```Now I will try to add the --store-quirks-as-lkw to have the conf stored forever I hope, and remove the uswsusp package to see if I stll need it.
The terrible thing in the pm-suspend man is this 2 stupid/dauntnig remarks being the cause I did not tried these options:```

**--quirk-vbemode-restore**
           This option will save and restore the current VESA mode which may
           be necessary to avoid X screen corruption. Using this feature on
           Intel graphics hardware is probably a bad idea.
**--quirk-vbe-post**
           This option will attempt to reinitialize the video card when
           resuming from suspend, using the same code the system BIOS uses at
           boot in order to initialize the video hardware. Not all video cards
           need this, and using this option on systems where it is not needed
           can cause a system to lock up when resuming.

```Whatever stupid or not, I would have never found the exact working config on my own without the help of a working release and its pm-suspend.log.
The other stupid thing is me : I paid a support to Canonical to get help to workaround this issue and they did not even help me like you did TOZ! They are even not able to send me an invoice for my payment :( Just wander is it a fake company? The only thing they said is that my system is not certified. If I remember well the story, the Linus' cheap computer for which he created Linux was not a certified Unix machine, wasn't it?

---

### Post by Byb on 2011-11-21
News: I removed uwssusp with no problems on suspend. Then I tried to remove quirks one by one. During these tests I met a strange behaviour : at a time, the login popup was completely bypassed, which can be considered as a security issue. I did not reboot the PC at the moment, so I can't already say this ~issue~ will go on. I must notice that in the lap time before I found how to make resume working, a new xserver-xorg-video-intel was found and installed by my update manager. I'll have to submit this info in launchpad and check in my working HDD if suspend work with the previous xserver and if the login bypass is present.
Thank you TOZ for the time you spent with me

[EDIT] : I just received the invoice from the Merchandise Mania (I just waited it since september 12th ! )... but unfortunatly, I paid in Euros and the invoice is in GBP ..... grrrrr, not suitable for my accounts

---

### Post by Toz on 2011-11-21
Good idea to try previous versions until you found one that works. Kudos to you.

To make this permanent, have a look at the **/usr/lib/pm-utils/video-quirks** directory. It is a database of quirks to use per system. The file **20-video-quirk-pm-fujitsu.quirkdb** seems most pertinent to you. There doesn't appear to me an entry for the M7405 - you could add one. The file appears to be pretty straight forward. **sudo dmidecode** will help identify the vendor name and other info needed for that file.

---

### Post by Byb on 2011-11-21
THanks Toz, I'll have a look and I hope this will help others. Although, I'm sure I don't understand a hundredth of what happened between Jaunty and Karmic to bring this regression, if a regression it is. should it help the s2ram guy to be informed of this via s2ram -i even if s2ram is not in the affair anymore?

---

### Post by Toz on 2011-11-21
Unfortunately I don't think s2ram is being atively developed anymore ([http://suspend.sourceforge.net/]("http://suspend.sourceforge.net/")).

---

### Post by Byb on 2011-11-22
Hi Toz
I'm having a look at 20-video-quirk database. Another mistake from me: I understand now it is only local, but the good thing is seems this would be the good place to keep the resume working over kernel changes, when the /var/cache/pm-utils/last_known_working.quirkdb file created by the pm-utils --store-quirks-as-lkw command would be ignored/deleted in such cases.
Although, my skills in scripts reading and in regexp is poor, so the files 20-video-quirk... are not so pretty straight forward to me ;). My difficulties here are my laptop manufacturer info from dmidecode is either FUJITSU, SIEMENS or FUJITSU SIEMENS (because of the blank inside) or even Uniwill at Base Board Information Manufacturer, and Product name is "Amilo M7405", but the match strings do not match in the file (system.hardware.vendor is vendor American Megatrend Inc. in dmidecode, and I see entries that may already [mis]match like 
```
match          regex ^FUJITSU
  match system.hardware.product regex_ncase amilo
   match system.hardware.product regex A1667G Serie|Pa 1510|Li 1718|M1425
```(knowing M1425 and M7405 are nearly the same)
```
match system.hardware.product regex ^M Series$
``````
match system.hardware.product regex AMILO M|A Series
    match system.hardware.version regex -1 |0\.01
``````

match system.hardware.product regex T2010
    match system.hardware.product regex ^FUJITSU SIEMENS$
```and this match/submatch that could be modified, all that is puzzleling me deeper, so I'll stick to the current kernel. Whatever I'm not yet ready in my tests to find what are minimum required quirks to pass to pm-utils. It is not clear to me if I must delete the last_known_working.quirkdb between  each pm-suspend --quirk... tests because I looked in the file and I saw none of the quirks I passed... maybe they are stored elsewhere. When I reach, I will try to lock all upgrades to my system because I would be too afraid to have to dig in that kind of issue again, it is far too much time consuming.

---

### Post by Byb on 2011-11-22
Toz, hope you're stll here :wink:, I think i'll need some other idea
NEWS: The suspend issue seems to have nothing to do with quirks : you  remember the story with my fresh-full-hdd-installs that drove me  learning suspend went broken when doing the step from Jaunty to Karmic. I  think I found the breaking thing is GRUB (which went from legacy to  GRUB2 in the step).
How I deduced this:
1) I searched when suspend  broke doing full installs on a spare ide ATA 20GB HDD I piked in a  broken PC to preserve my ~working~ 80GB drive. This learnt me the gap  was at Karmic step. OK all this I can reproduce.
2) At this time I had a reformated whole drive allocated to Oneiric. I later added the  3.2.0rc2 kernel for Launchpad submit issue purpose. Notice that at this  time GRUB2 is the boss here in.
3) I tried a CD iso for bios  compatibility (using Ubuntu 7.04 among other distros), then I tried  LiveCD 7.04 (which had no suspend/resume out of the box, so I discarded  it, also because very old), and then I installed a fresh Jaunty (I just  forgot to inform you that I kept the Oneiric on the disk) in which I  confirmed resume was working. Just after this I learnt the quirks in  pm-suspend.log, and I switched to Oneiric to test them...they worked,  and I got your undeserved kudos :wink:.  At this time I was bored (but I did not talked you about) with the  horrible localized-broken (like the Jaunty GUI - no more localization  available) GRUB-legacy menu that began the new boss of the drive since I  installed the additional Jaunty, so I reinstalled GRUB2 from Oneiric  and began my tests to find the minimum quirks really required. After  many trials, no combination worked, even the one with the 6 quirks  previously found in Jaunty log. ...:confused:...  so I switched to Jaunty (remember, with GRUB2, for the first time in my  life): resume did not work neither from GUI nor from sudo terminal.
4)  I made a backup copy of /boot/grub/menu.lst because os-prober was no  longer available for Jaunty and I'm poorly easy in grub things (and also  because of my azerty keyboard making things worse when it comes to work  in grub commands at boot time), and I did a sudo grub-install /dev/sda  to switch back to GRUB-legacy.
5) I restarted (noticed I lost the  3.0.0-13 kernel installed in the lap time, don't matter) went in Jaunty,  found resume works again, switched to 3.0.0-12, found resume works  out-of-the-box-with-absolutely-no-quirks :!:, switched to 3.2rc2, same seamless resume.

I'll now google grub+resume, but if you have any idea, you are still welcome in the hunt. ):P

---

### Post by Toz on 2011-11-22
Very interesting indeed. Unfortunately, I haven't come across this in the past. However, your test prove this to be the case. Its always been interesting to me how (with grub2) there is no indication of system returning from suspend. If it were a quirks problem, you usually get some indication in the logs that resume was attempted.

I will also look around for more information. In the meantime, can you post the **/boot/grub/grub.cfg** (grub2) and **/boot/grub/menu.lst** (grub1) files so I can see if there is some difference?

---

### Post by Toz on 2011-11-22
Here is an interesting link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711").

Post #33 fixed problem by purging grub2 and reverting to grub-legacy. Instructions here: [https://help.ubuntu.com/community/Grub2#Reverting_to_GRUB_Legacy]("https://help.ubuntu.com/community/Grub2#Reverting_to_GRUB_Legacy").

Post #119 suggests using the kernel parameter **intel_idle.max_cstate=0** to offset potential CPUIdle cause (not grub-related that I can see, but maybe worth a try).

And this interesting thread too: [http://askubuntu.com/questions/17079/what-is-grubs-2-role-in-the-suspend-hibernate-process]("http://askubuntu.com/questions/17079/what-is-grubs-2-role-in-the-suspend-hibernate-process").

---

### Post by Byb on 2011-11-23
Hi Toz, the intelidlemaxcstate did nothing.
About the post reverting to grub legacy, it is what I discovered when i installed Jaunty beside existing Oneiric.
Here are the files you asked. I had a look to see if something would be incoherent, but as I'm built from ignorance and presupositions, this dooesn't helps at all.
As I say in the end of the file 4 - ...   would it be GRUB1/GRUB2 passing different parameters to same kernel?

---

### Post by Toz on 2011-11-23
> **Byb said:**
> would it be GRUB1/GRUB2 passing different parameters to same kernel?

Thats what I was wondering, but I don't think its related to the UUID. However, just to confirm, can you run these commands on oneiric kernel 3.0.0.13 with _both_ grub-legacy and grub2:

```
cat /proc/cmdline
```
...and
```
cat /etc/initramfs-tools/conf.d/resume
```
...and
```
sudo blkid
```
...and
```
sudo lspci -k
```

---

### Post by Byb on 2011-11-23
Hello Toz, Good morning Toronto!
The **/boot/grub/grub.cfg** (grub2) and **/boot/grub/menu.lst** you asked in post #42 are in the files above, both seen from each 4 GRUB1|2|Jaunty|Oneiric combinations (was a huge job) so you can see 4*4 files: the 4 in the currently booted combination, times the 4 in the unbooted one each time, i.e. the ones in /media/disk/etc|boot ... or /media/uuid... with the issued commands. I also added /etc/defaut/grub each 4 time and other grub related info
> **Toz said:**
> Thats what I was wondering, but I don't think its related to the UUID. However, just to confirm, can you run these commands on oneiric kernel 3.0.0.13 with _both_ grub-legacy and grub2:

```
cat /proc/cmdline
```
Gime two minutes
> ...and
```
cat /etc/initramfs-tools/conf.d/resume
```
in the files above (GRUB2=file 2 ; legacy=file4)
> ...and
```
sudo blkid
```
in the files above (GRUB2=file 2 ; legacy=file4)
> ...and
```
sudo lspci -k
```Gime two more minutes.
See you soon

---

### Post by Byb on 2011-11-23
From GRUB legacy (resume OK)
```
uname -r
3.0.0-13-generic
moi@moi-Amilo-M7405:~$ cat /proc/cmdline
root=UUID=d1565e0c-2dcb-4ebf-8326-0a28127b78f0 ro 
moi@moi-Amilo-M7405:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=5f0839d7-7b2f-41d3-a635-927a7861308d
moi@moi-Amilo-M7405:~$ sudo blkid
[sudo] password for moi: 
/dev/sda1: UUID="d1565e0c-2dcb-4ebf-8326-0a28127b78f0" TYPE="ext4" 
/dev/sda5: UUID="5f0839d7-7b2f-41d3-a635-927a7861308d" TYPE="swap" 
/dev/sda6: UUID="78e4a6bf-ecb4-40c6-b822-0ebd3567cdaa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="cc611fc4-d6fb-4634-9f91-a695e1af737e" TYPE="swap" 
moi@moi-Amilo-M7405:~$ sudo lspci -k
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: agpgart-intel
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: snd-intel8x0m
01:03.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
01:03.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
01:03.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
    Subsystem: Fujitsu Technology Solutions Device 106a
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2702
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
```then for the next post: ```
sudo grub-install /dev/sda
Installation finished. No error reported.
```Please wait I reboot

---

### Post by Byb on 2011-11-23
And from GRUB2 (resume KO):
```
moi@moi-Amilo-M7405:~$ uname -r
3.0.0-13-generic
moi@moi-Amilo-M7405:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=d1565e0c-2dcb-4ebf-8326-0a28127b78f0 ro
moi@moi-Amilo-M7405:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=5f0839d7-7b2f-41d3-a635-927a7861308d
moi@moi-Amilo-M7405:~$ sudo blkid
[sudo] password for moi: 
/dev/sda1: UUID="d1565e0c-2dcb-4ebf-8326-0a28127b78f0" TYPE="ext4" 
/dev/sda5: UUID="5f0839d7-7b2f-41d3-a635-927a7861308d" TYPE="swap" 
/dev/sda6: UUID="78e4a6bf-ecb4-40c6-b822-0ebd3567cdaa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="cc611fc4-d6fb-4634-9f91-a695e1af737e" TYPE="swap" 
moi@moi-Amilo-M7405:~$ sudo lspci -k
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: agpgart-intel
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel modules: snd-intel8x0m
01:03.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
01:03.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
01:03.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
    Subsystem: Fujitsu Technology Solutions Device 106a
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2702
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Fujitsu Technology Solutions Device 106a
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
```

---

### Post by Toz on 2011-11-23
Well, I fail to see anything that would cause this discrepancy in your configuration files - yet there must be something about how grub-legacy and grub2 work that is affecting you. I'm afraid I have no further ideas on fixing this. Is using grub legacy (instead of grub2) an option for you?

---

### Post by Byb on 2011-11-23
It is the only way I see Toz. Thank you for your help

---

### Post by Byb on 2012-03-28
I gave new try today with 3.3.0.999-20120325-0407 kernel, and it works OK :)
So the issue found a solution between 3.2-rc2 and the above.

So I think now my old 2004 laptop is ready to die :(

Bye bye Toz

---

