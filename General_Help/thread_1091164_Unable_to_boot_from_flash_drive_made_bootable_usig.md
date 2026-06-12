---
title: "Unable to boot from flash drive made bootable usign Ubuntu 8.10"
date: 2009-03-09
forum: General Help
---

### Post by smshinde on 2009-03-09
Dear All,
I have installed Ubuntu 8.10 on my PC.
i am having Transcend 1 GB pen drive. Using the Flash Drive Bootable creation utility i have created the bootable flash drive SUCCESSFULLY.

Then I choose USB HDD as boot option and tried to boot. I presents me with a :boot option.
Then whenever I pressed  enter or any other text, I got message like 'linux boot image not found.'
What to type on the boot: prompt?

Please help me in this matter.


-Sameer

---

### Post by C.S.Cameron on 2009-03-09
How old is your computer?
Not all computers whose BIOS allows booting from USB HDD will boot from flash drive.
Some BIOS prefers selecting the flash drive as the first HDD.

---

### Post by smshinde on 2009-03-09
It is the newer one Intel P4 so I think there is no issue as such. There are more than one options related to USB as a bootable device USB HDD, USB flash, USB CD etc. Which is the most appropriate to choose from?
Waiting for your reply.

-Sameer

---

### Post by C.S.Cameron on 2009-03-17
On my laptop for example, with American Megatrends v02.56 BIOS, I go to Boot, Hard Disk Drives, and then select [Kingston DataTrave] as 1st Drive, similar on my office computer. Both boot the flash drives.
On an older computer with AMIBIOS 1.21.12, if I go to Advanced Setup, 1st Boot Device, I get a choice of USB HDD, USB CDROM, USB FDD, etc, (But no USB Flash). and it will not boot the flash drive except by using a boot CD.
Have you tried selecting USB Flash in your BIOS?

---

