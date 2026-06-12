---
title: "[SOLVED] DIFFERENT Audio problem after kernal update"
date: 2008-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tanya_814 on 2008-10-16
Hi,

I have a 1525 inspiron and downloaded the same kernel update as many of you.
I had the same audio problems. 
The only thing is, nothing is working for me.
I tried this:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

...but it didn't work. I even switched from the '17 generic' to the '21 generic' (the one for my computer).
I think I need to reinstall my sound card.

This is what happens when I paste all the above stuff into my terminal box. (Sorry, I'm not too good with computers. My terms are pretty bad...haha)
----------------------
tanya@dell-desktop:~$ cd /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
[sudo] password for tanya: 
mv: cannot stat `snd-hda-intel.ko.REPLACEDBYhsfmodem': No such file or directory
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda$ cd /lib/modules/2.6.24-21-generic/updates
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/updates$ sudo rm snd-hda-intel.ko
rm: cannot remove `snd-hda-intel.ko': No such file or directory
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/updates$ sudo rm snd-hda-codec.ko
rm: cannot remove `snd-hda-codec.ko': No such file or directory
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/updates$ sudo depmod -a
tanya@dell-desktop:/lib/modules/2.6.24-21-generic/updates$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
-------------------

This is all before the reboot command. 
Now, I already did this a few times. Could it be that it doesnt recognize what it already removed?
Also, another question. Would it be harmful to go back and use my computer with the previous kernel?


Any help would be greatly appreciated. :)

---

### Post by Anditsu on 2008-10-16
I have same model and problem. I'm hopeing they will have a patch

---

### Post by Denny Johnson on 2008-10-17
> **tanya_814 said:**
> 
Also, another question. Would it be harmful to go back and use my computer with the previous kernel?


That's what I did until I got the bugs worked out, no problems.

---

### Post by StewartM on 2008-10-17
Tanya,

Just checking the replies on the Ubuntu forums as well as the Dell.

Let me know if the snd-hda-intel.ko file I sent from my working 1525N fixes your problem.

StewartM

---

### Post by moshuptrail on 2008-10-17
with the dell 1525 you press ESC while booting and it will show the menu
simply select the -19 version of the kernel to boot (instead of -21)

a little research and you can learn how to edit your 
/boot/grub/menu.lst
and change that to the default

That WILL get the sound back.

---

### Post by tanya_814 on 2008-10-17
It's fixed! YAY!

---

### Post by Andy Moon on 2008-10-18
Hello,

I had the same audio problem as Tanya. Fixed it thanks to the Dell Wiki link she provided :

> **tanya_814 said:**
> Hi,

I have a 1525 inspiron and downloaded the same kernel update as many of you.
I had the same audio problems. 
The only thing is, nothing is working for me.
I tried this:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

...but it didn't work. I even switched from the '17 generic' to the '21 generic' (the one for my computer).
I think I need to reinstall my sound card.


Here's a summary of how it worked in my case, if that can help others :

_Computer : _
Inspirion 1525
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

_OS :_
Ubuntu Hardy 8.04
Kernel Linux 2.6.24-19-generic UPGRADED TO 2.6.24-21-generic => that's when I encountered the sound problem
[U]
The problem[/U]

After I upgraded to kernel 2.4.24-21, I had no sound anymore. Some symptoms :
there was a red warning flag on my sound icon tray
no driver found by ubuntu, as revealed by the shell command 
"aplay -l" (result was something like :  device_list:221: no soundcard found...)


_What solved my problem_

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

Quotes from that page :
```
Description: No sound after upgrade from Ubuntu 7.10 or upgrade to kernel 2.4.24-17
Systems Affected: Inspiron E1505n, 1420n and 1525n.
```
=>this procedure also fixes the problem after upgrade to kernel 2.4.24.-21


Follow the instructions given in the second part, titled _"If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic"_. 

Shall fix it for you too ;)

Cheers,

Andy

---

