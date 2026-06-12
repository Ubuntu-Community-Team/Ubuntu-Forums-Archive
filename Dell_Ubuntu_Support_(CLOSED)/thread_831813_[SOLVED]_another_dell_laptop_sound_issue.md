---
title: "[SOLVED] another dell laptop sound issue"
date: 2008-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bryncoles on 2008-06-17
many apologies if this issue has been dealt with to death! this morning i received my brand-spanking new dell insiron 1525 preinstalled with gutsy. (this is my official 'no more windows on my home computer' moment!). 

i was confident of two things: that sound would break when i upgraded to hardy, and that the documentation would see me through no worries. 

i was half right! ;-)

so, double clicking on the speaker icon in the top left gets me the following message:

```
No volume control GStreamer plugins and/or devices found
```

while following the instructions on dell's website stalls with the following error:

```
bryn@dell-desktop:~$ sudo dpkg -r hsfmodem
[sudo] password for bryn: 
(Reading database ... 110034 files and directories currently installed.)
Removing hsfmodem ...
bryn@dell-desktop:~$ sudo dpkg -r linux-backports-modules-2.6.22-14-generic
(Reading database ... 109903 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
bryn@dell-desktop:~$ cd /lib/modules/'uname -r'/ubuntu/sound/alsa-driver/pci/hda
bash: cd: /lib/modules/uname -r/ubuntu/sound/alsa-driver/pci/hda: No such file or directory
```

any ideas anyone? if there are already answers to these issues and i have just missed them, feel free to admonish my 'googling skillz', and point me in the right direction. 

*edit*

just spotted this thread 

```
http://ubuntuforums.org/showthread.php?t=813957
```. how do you get the blushing icon? 

it feels good to get a brank spanking new ubuntu pre-installed!

*edit*

solved this by trying the dell website instructions again and this time, cutting and pasting. i feel so foolish!

---

