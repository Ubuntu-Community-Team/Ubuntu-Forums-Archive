---
title: "Lubuntu 11.10 Brightness issue"
date: 2011-10-16
forum: Desktop Environments
---

### Post by decomp on 2011-10-16
Hi All!

I am running Lubuntu 11.10 and when my display turns off, the screen does not return to full brightness afterwards. It is only  half brightness and I cannot get it to full again. The function keys are working but will not go any higher than halfway brightness.

The problem is with xfce4-power-manager but I'm not sure what.

I have not had this problem in debian+lxde or ubuntu 10.10+lxde.

Anyone else have this issue? why wont xfce4-power-manager return my screen to full brightness anymore?

---

### Post by decomp on 2011-10-16
Still can't figure this one out :(

---

### Post by TutenStain on 2011-10-16
> **decomp said:**
> Hi All!

I am running Lubuntu 11.10 and when my display turns off, the screen does not return to full brightness afterwards. It is only  half brightness and I cannot get it to full again. The function keys are working but will not go any higher than halfway brightness.

The problem is with xfce4-power-manager but I'm not sure what.

I have not had this problem in debian+lxde or ubuntu 10.10+lxde.

Anyone else have this issue? why wont xfce4-power-manager return my screen to full brightness anymore?

Same here on my laptop Ubuntu 11.10 GNOME 3.

---

### Post by amjjawad on 2011-10-16
Hi there,

I'm a member of Lubuntu Team and I'll be very glad to help :)
I'll do some search for your problem guys and get back to you as soon as I can. I'm leaving now and it's too late here already. Will keep you posted ;)

Thanks for using Lubuntu :)

---

### Post by amjjawad on 2011-10-16
> **TutenStain said:**
> Same here on my laptop Ubuntu 11.10 GNOME 3.

Sorry but your problem is different that the Original Poster's Problem. He/She is using Lubuntu while you are using Ubuntu. Two different Desktop Environemnt.

Please search the forum for a similar case to yours and if you couldn't find, try here: [www.googlubuntu.com](www.googlubuntu.com).
If you couldn't find, start your own thread :)

Thanks!

---

### Post by decomp on 2011-10-18
So I disabled xfce4-power-manager at startup and it's still happening so it's not the power manager.

Saw something about acpi somewhere? 

Saw an old suggestion [_here_]("http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/") but it didn't work for me.

---

### Post by llelectronics on 2011-10-18
You could try xbacklight to adjust the brightness.

---

### Post by decomp on 2011-10-19
> **llelectronics said:**
> You could try xbacklight to adjust the brightness.

That did the trick! Your a savior! I can use my computer! Now if I could only figure out what's causing it..

Edit: Ooh I am also totally binding this to a hot key.

---

### Post by dondada on 2011-12-18
I've been experiencing this same dark screen issue on my eeePC 1005 HAB running Lubuntu 11.10. It actually only started happening recently - like a month ago.

xbacklight has solved this for now.

---

### Post by amjjawad on 2011-12-21
> **decomp said:**
> That did the trick! Your a savior! I can use my computer! Now if I could only figure out what's causing it..

Edit: Ooh I am also totally binding this to a hot key.

Kindly mark your thread as SOLVED:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

Thank you :)

---

### Post by decomp on 2012-01-06
Well I still wouldn't say it's solved.. it's a nice little fix but it's pretty messy and doesn't resolve the original issue.

Also I recently tested out standard ubuntu 11.10 and had the same issue.

---

### Post by rodrigo.miguel on 2012-02-15
Might help:

Brightness control for Lubuntu / LXDE (when the Fn key does not work)

[http://linuxlike.blogspot.com/2012/0...untu-lxde.html](http://linuxlike.blogspot.com/2012/0...untu-lxde.html)

---

### Post by satanicat on 2012-03-19
Hello everyone.
I have the exact same problem with lubuntu on my netbook and i could not solve it using xbacklight (backlight wouldnt do anything when i put the command "xbacklight -set -%100" or anything simillar to that.

anyone can help me? what can it be?


Thanks.

PS: a cute picture of my cat as a present. 
[http://i.imgur.com/QpO8D.jpg](http://i.imgur.com/QpO8D.jpg)

---

### Post by Toz on 2012-03-19
Hello and welcome to the forums, satanicat.

What is the make and model of your netbook?
And can you open a terminal window, type in the following commands, and post back the results:
```

cat /proc/cmdline
sudo lspci -vnn | grep -A10 VGA
ls /sys/class/backlight
lsmod

```

---

### Post by satanicat on 2012-03-20
> **Toz said:**
> Hello and welcome to the forums, satanicat.

What is the make and model of your netbook?
And can you open a terminal window, type in the following commands, and post back the results:
```

cat /proc/cmdline
sudo lspci -vnn | grep -A10 VGA
ls /sys/class/backlight
lsmod

```

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device [144d:c08f]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915


---------------------


Here it is.
Also, its a Samsung n145 Plus netbook.
Thank you.

---

### Post by Toz on 2012-03-20
Have a look at this PPA: [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa") and this forum ([http://www.voria.org/forum/search.php?sid=fc01402965f05626132020cedcdbd3c8]("http://www.voria.org/forum/search.php?sid=fc01402965f05626132020cedcdbd3c8")). It seems to fix the brightness issue on samsung netbooks.

EDIT: Here is another link: [https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783]("https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783")

---

### Post by satanicat on 2012-03-21
> **Toz said:**
> Have a look at this PPA: [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa") and this forum ([http://www.voria.org/forum/search.php?sid=fc01402965f05626132020cedcdbd3c8]("http://www.voria.org/forum/search.php?sid=fc01402965f05626132020cedcdbd3c8")). It seems to fix the brightness issue on samsung netbooks.

EDIT: Here is another link: [https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783]("https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783")

Toz, i did all that and maybe more and i thought i've solved it.
the brightness was ok and everything. but sometimes, i close the lid and after opening it again the screen looks messed up (looks like double screens looking bad) of course that when i restart, everything seems to be ok again. Well.. the brightness issue comes and goes, now, for example, it was functional in the morning, i closed the lid and the thing with the screen happened after i opened it. now the brightness is at 50% and nothing happens when i move it.

im trying to convince myself all this is a software bug, i dont see how the hardware can be wrong.



Please help.


Do you think i should install another distro?

Maybe there are alternative samsung drivers to download?

sorry if i messed up with the english.

-
Also, i want to disable the scrolling (because its all messed up and it jumps up all the time) so i go to gpointing-device-settings and i see "two finger scroll" is disabled. so i have to enable it, and then disable it again. only then the scrolling is disabled.


is there a less stupid way to solve it?


cheers.

---

### Post by Toz on 2012-03-21
> **satanicat said:**
> Toz, i did all that and maybe more and i thought i've solved it.
the brightness was ok and everything. but sometimes, i close the lid and after opening it again the screen looks messed up (looks like double screens looking bad) of course that when i restart, everything seems to be ok again.
Does your computer go to sleep (suspend) or hibernate when you close the lid? 
> Well.. the brightness issue comes and goes, now, for example, it was functional in the morning, i closed the lid and the thing with the screen happened after i opened it. now the brightness is at 50% and nothing happens when i move it.
The second link ([https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783]("https://www.ultimateeditionoz.com/forum/viewtopic.php?p=21783")) had some further instructions involving setting kernel parameters in the grub line and adjusting udev rules. Did you follow those steps as well?

> im trying to convince myself all this is a software bug, i dont see how the hardware can be wrong.
I would tend to agree.



> Please help.


Do you think i should install another distro?
The choice is yours. Since I don't own a samsung netbook, I can't comment. However, from the link above, it looks like ubuntu should work fine with your netbook once its configured properly.

> Maybe there are alternative samsung drivers to download?

sorry if i messed up with the english.
No worries. Lets see if we can get this to work first.

> -
Also, i want to disable the scrolling (because its all messed up and it jumps up all the time) so i go to gpointing-device-settings and i see "two finger scroll" is disabled. so i have to enable it, and then disable it again. only then the scrolling is disabled.


is there a less stupid way to solve it?


cheers.
Try this:
1. Create a script to disable the scrolling:
```
gksudo leafpad /usr/local/bin/disable_scroll
```

2. Copy & Paste this information into the file:
```

#!/bin/bash

/usr/bin/synclient VertTwoFingerScroll=0
/usr/bin/synclient HorizTwoFingerScroll=0

```

3. Save the file.

4. Make the file executable:
```
sudo chmod +x /usr/local/bin/disable_scroll
```

5. Add this new script (/usr/local/bin/disable_scroll) to your startup files. This might help: [http://wiki.lxde.org/en/Autostart]("http://wiki.lxde.org/en/Autostart")

---

### Post by satanicat on 2012-03-21
What is a .desktop file?

(im tying to follow this part...[http://wiki.lxde.org/en/Autostart](http://wiki.lxde.org/en/Autostart))


By the way, thanks for your help!

Also, no, the netbook does nothing when i close the lid (as i wanted it to be)

> The second link ([https://www.ultimateeditionoz.com/fo...ic.php?p=21783](https://www.ultimateeditionoz.com/fo...ic.php?p=21783)) had some further instructions involving setting kernel parameters in the grub line and adjusting udev rules. Did you follow those steps as well?


I think i've made all that, i've found that info in some other pages too and seems to do nothing.

Well.. as i told you, the problem was solved for an instance.




-
If i upgrade to Oneric Ocelot, i would upgrade to ubuntu or it will be lubuntu: oneric ocelot?

dont laugh at me.


haha, cheers.

---

### Post by satanicat on 2012-03-21
```
$ ln -s /usr/local/bin/disable_scroll ~/.config/autostart/ 
```

Is that correct?

edit:

derp, i have to create the directory first, right?


Any clue about the screen messing up?

---

### Post by Toz on 2012-03-21
I'm sorry but I don't use lubuntu, so I'm just going by the instructions in that link. First try running the script to see if it properly disables the two finger scroll:
```
/usr/local/bin/disable_scroll
```

If it works, try this:
```

leafpad ~/.config/autostart/disable_scroll.desktop
```
...with the following content:
```

[Desktop Entry] 
Type=Application
Exec=/usr/local/bin/disable_scroll

```
...and reboot to test.

---

### Post by Toz on 2012-03-21
> **satanicat said:**
> Any clue about the screen messing up?

When the screen is messed up, try Ctrl+Alt+F1 to go to TTY1 then Ctrl+Alt+F7 to return back to the GUI. Does this fix the problem?

---

### Post by satanicat on 2012-03-22
> **Toz said:**
> When the screen is messed up, try Ctrl+Alt+F1 to go to TTY1 then Ctrl+Alt+F7 to return back to the GUI. Does this fix the problem?

Totally works man!  :guitar:

---

### Post by Toz on 2012-03-22
Interesting. So then something must be happening when you close the lid. Can you post back the contents of the /var/log/pm-suspend.log file? I'm curious to see if it has some clues. 

And can you also post back the contents of:
- ~/.xsession-errors
- /var/log/Xorg.0.log

---

### Post by miegiel on 2012-03-22
Maybe I shouldn't butt in, but I put this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```
in my */etc/default/grub* to make my backlight work (eee netbook running debian testing).

**ps** I forgot to add that you need to run 
```
sudo update-grub
```
in the terminal to make the change to GRUB take effect and reboot.


A bit stupid of me ](*,) to leave that out, not everyone's familiar with making changes to grub.

---

### Post by satanicat on 2012-03-24
> **Toz said:**
> Interesting. So then something must be happening when you close the lid. Can you post back the contents of the /var/log/pm-suspend.log file? I'm curious to see if it has some clues. 

And can you also post back the contents of:
- ~/.xsession-errors
- /var/log/Xorg.0.log

Here you go.

pm-suspend.log [http://pastebin.com/e3WskxcB](http://pastebin.com/e3WskxcB)

xorg.0.log [http://pastebin.com/yzzTbFJ2](http://pastebin.com/yzzTbFJ2)

.xsession-errors [http://pastebin.com/Djh6B5fD](http://pastebin.com/Djh6B5fD)

---

### Post by satanicat on 2012-03-24
> **miegiel said:**
> Maybe I shouldn't butt in, but I put this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```
in my */etc/default/grub* to make my backlight work (eee netbook running debian testing).

I did that before and nothing changed.


> **miegiel said:**
> 
**ps** I forgot to add that you need to run 
```
sudo update-grub
```
in the terminal to make the change to GRUB take effect and reboot.


A bit stupid of me ](*,) to leave that out, not everyone's familiar with making changes to grub.


OHHHHHHH interesting.

gonna reboot now.

---

### Post by satanicat on 2012-03-24
Still can't change the brightness but it seems at %100 now.

---

### Post by satanicat on 2012-03-25
Now it seems at %50 again. 
what a nightmare.

(bump)

---

### Post by Toz on 2012-03-26
> **satanicat said:**
> Here you go.

pm-suspend.log [http://pastebin.com/e3WskxcB](http://pastebin.com/e3WskxcB)

xorg.0.log [http://pastebin.com/yzzTbFJ2](http://pastebin.com/yzzTbFJ2)

.xsession-errors [http://pastebin.com/Djh6B5fD](http://pastebin.com/Djh6B5fD)

According to your pm-suspend.log file, your notebook is suspending when you close the lid. 

Just to confirm: Does brightness work okay when you power-up your notebook? Function keys and all? 

And does it only go screwy after you close the lid?

---

### Post by satanicat on 2012-03-26
The netbook does nothing when i close the lid. im pretty sure about that.

the brightness sometimes starts at 50% and sometimes at 100%, in both cases the ammount of brightness cant be changed. (but pressing Fn + left / right arrow shows the brightness bar moving left and right, changing nothing)

---

### Post by Toz on 2012-03-26
> **satanicat said:**
> The netbook does nothing when i close the lid. im pretty sure about that.
Lets determine this for sure. First, clear out the pm-suspend.log file:
```
sudo mv /usr/log/pm-suspend.log /usr/log/pm-suspend.log.BAK
```
..then close the lid. Wait 1 minute and open it again. Was a new /var/log/pm-suspend.log file created and if so, what are the contents? If there is no new log file, then it didn't suspend.

> the brightness sometimes starts at 50% and sometimes at 100%, in both cases the ammount of brightness cant be changed. (but pressing Fn + left / right arrow shows the brightness bar moving left and right, changing nothing)

Lets see if we can get a workaround to work. Can you post back the results of the following commands:
```

lsmod
cat /proc/cmdline
ls /sys/class/backlight
sudo lspci -vnn | grep -A10 VGA

```

---

### Post by satanicat on 2012-03-26
> **Toz said:**
> 


Lets see if we can get a workaround to work. Can you post back the results of the following commands:
```

lsmod
cat /proc/cmdline
ls /sys/class/backlight
sudo lspci -vnn | grep -A10 VGA

```

pascual@satanico:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
ath9k                 103633  0 
snd_hda_intel          24113  7 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_intel,snd_hda_codec
mac80211              257001  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19141  2 ath9k,ath9k_hw
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
samsung_backlight      13487  0 
cfg80211              156212  3 ath9k,mac80211,ath
snd_timer              28659  4 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
snd                    55295  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  451053  2 
ahci                   21591  4 
drm_kms_helper         40971  1 i915
libahci                25548  1 ahci
sky2                   49172  0 
drm                   184164  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
pascual@satanico:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-13-generic root=UUID=0284ff86-656b-48b7-9dfc-be91cebac492 ro acpi_sleep=nonvs quiet acpi_osi=Linux acpi_brightness=vendor splash vt.handoff=7
pascual@satanico:~$ ls /sys/class/backlight
acpi_video0  samsung
pascual@satanico:~$ sudo lspci -vnn | grep -A10 VGA

---

### Post by Toz on 2012-03-27
> **satanicat said:**
> pascual@satanico:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
ath9k                 103633  0 
snd_hda_intel          24113  7 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_intel,snd_hda_codec
mac80211              257001  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19141  2 ath9k,ath9k_hw
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
samsung_backlight      13487  0 
cfg80211              156212  3 ath9k,mac80211,ath
snd_timer              28659  4 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
snd                    55295  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  451053  2 
ahci                   21591  4 
drm_kms_helper         40971  1 i915
libahci                25548  1 ahci
sky2                   49172  0 
drm                   184164  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
Thanks
> pascual@satanico:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-13-generic root=UUID=0284ff86-656b-48b7-9dfc-be91cebac492 ro acpi_sleep=nonvs quiet acpi_osi=Linux acpi_brightness=vendor splash vt.handoff=7
Can you try removing the **acpi_osi=Linux acpi_brightness=vendor** kernel parameters from /etc/default/grub, rerunning "sudo update-grub", rebooting, and seeing whether the brightness keys work now?

And if not, try adding "acpi_backlight=vendor" (notice its backlight, not brightness), rerunning "sudo update-grub", rebooting and checking again.

> pascual@satanico:~$ ls /sys/class/backlight
acpi_video0  samsung
If the above kernel parameters don't work, run these commands and post back the results:
```
cat /sys/class/backlight/acpi_video0/max_brightness
cat /sys/class/backlight/acpi_video0/brightness
cat /sys/class/backlight/samsung/max_brightness
cat /sys/class/backlight/samsung/brightness
```
> pascual@satanico:~$ sudo lspci -vnn | grep -A10 VGA
Were there no results? It should have responded with something.

---

### Post by satanicat on 2012-03-27
I just updated to 11.10 and the brightness keys are working.

it takes a little more the turning off, but meh.


also..
is there any software center for lubuntu? i want to install some apps that i cant.

---

### Post by Toz on 2012-03-28
> **satanicat said:**
> is there any software center for 
lubuntu? i want to install some apps that i cant.

Its the same software centre for all *buntus. Which apps are you trying to install?

---

### Post by satanicat on 2012-03-28
edit: nothing now, thanks, everything taken care of.

---

### Post by Rock Storm on 2012-12-09
I already posted a solution in another thread which I believe refers to the same issue.

[http://ubuntuforums.org/showthread.php?p=12395614#post12395614](http://ubuntuforums.org/showthread.php?p=12395614#post12395614)

---

