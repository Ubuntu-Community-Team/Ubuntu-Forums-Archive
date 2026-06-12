---
title: "Abit AG8 Shutdown problem"
date: 2009-02-03
forum: Desktop Environments
---

### Post by revival on 2009-02-03
Hello all,

I have a problem with **Ubuntu Hardy 8.10** shutdown. On my PC when I click the shutdown button, it looks like the shutdown process is going correctly but it is never able to complete the shutdown. The system goes always in text mode with cursor blinking and power on. The only thing I can do is to to switch off manually.

I did some reading in the forums and some people had similar shutdown problems so I tried their fixes to see if that would work out my problem, but I was unlucky. Among other things that I tried, I verified that hal was installed, I changed the /boot/grub/sources.lst and tried adding some option at the end of the boot line (I tried acpi=off and acpi=force) but didn't work. 

I have a mobo **Abit AG8** working with a PIV 3.2Ghz and a Nvidia 6200 Graphic Card. Attached is a file with the **lshw command output**.

Any help would be appreciated. Thanks in advance!

---

### Post by revival on 2009-03-02
SOLVED! (would be better to say, it is a WORKAROUND). Here is the solution (credit to [Nucleus2008]("http://ubuntuforums.org/member.php?u=612934")):

1. ENABLE SYSRQ KEYS
====================
open a terminal
edit "/etc/sysctl.conf" and append "kernel.sysrq=1"
call "sudo sysctl -p"

2. SHUTDOWN
=============
the default shutdown command in "/etc/init.d/halt" is "halt -d -f -i $poweroff $hddown".
edit "/etc/init.d/halt" and comment out that line
add the following 3 lines afterwards:

echo s > /proc/sysrq-trigger
sleep 1
echo o > /proc/sysrq-trigger

**_DONE!!!_** :guitar:

Additional information:

The "/proc/sysrq-trigger" can be used to make sysrq key calls just like if you were pressing the corresponding shortcut (i.e. Alt + PrintScr + s).

"s" attempts to sync all mounted filesystems. This shouldn't be necessary since "/etc/init.d/halt" is only called after all filesystems are unmounted. But it does no harm - so better be safe

"o" attempts to power down if your system supports it (this should be the case if power down worked for you before everything got screwed).

**WARNING:** "o" will power down immediately and doesn't care about unsynced filesystems, so make sure filesystems are unmounted should you want to try that shortcut manually!

---

