---
title: "UBuntu boots automatically in 9 secs"
date: 2009-03-22
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-03-22
well my family can't use ubuntu, and i dual boot with windows xp and ubuntu 
and when i turn on my computer , it gives me about 9 seconds to choose what OS to boot into and if i dont choose anything, it goes into linux automatically, how do i make it so it boots into windows xp after 9 secs rather than linux ubuntu, if its impossible im just gonna have to uninstall linux ubuntu :(
and btw how do i uninstall ubuntu?:o

---

### Post by Therion on 2009-03-22
It's do-able...

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

And you can't un-install an OS.  Overwrite it? Yes... Uninstall it? No.

---

### Post by Ericyzfr1 on 2009-03-22
On your option screen, where you can choose between Ubuntu and XP count from the top starting with 0, for example if XP is the third item down the list it is in fact "2".
sudo gedit menu.lst

in the section ##Num default, assign the number for XP and save. Note that if kernel are upgraded, you may have to the above again.

---

### Post by Deathray on 2009-03-22
> **tanveerahmed2k8 said:**
> well my family can't use ubuntu, and i dual boot with windows xp and ubuntu 
and when i turn on my computer , it gives me about 9 seconds to choose what OS to boot into and if i dont choose anything, it goes into linux automatically, how do i make it so it boots into windows xp after 9 secs rather than linux ubuntu, if its impossible im just gonna have to uninstall linux ubuntu :(
and btw how do i uninstall ubuntu?:o

Use the XP cd to issue the "fixmbr" command. After that delete the partition inside of XP and either create a new partition, or use a tool like Parition Magic to extend the C: partition.

---

### Post by themusicalduck on 2009-03-22
You could try looking for 'Startup manager' in the repositories and installing it (if it isn't by default). That gives you a gui that lets you change settings like timeout and default OS.

It'll probably be under either administration or preferences after installing it.

---

### Post by 3Miro on 2009-03-22
You can install a GRUB editor program and edit the Boot menu with it. You can change the umber of seconds and many other options.

---

### Post by fooman on 2009-03-22
if you would like a gui to make the change....open synaptic (system > administration > synaptic package manager) and search for "startupmanager".  when it finds it...right click on it and choose "mark for installation".

after it installs,  find it under system > administration > startup-manager

open it and click the boot options tab.... under the default operating system choose windows.

hope that helps.

edit....i am slow,  themusicalduck beat me to it!

---

### Post by sekinto on 2009-03-22
Press alt+F2 in Ubuntu and enter:
```
gksudo gedit /boot/grub/menu.lst
```Then press run or hit enter.
It should open up a text editor with your boot configuration file opened.

Here is mine (I removed a lot of things so only the important things remain, wherever there is a [...] that means I removed something to make it easier to show you what to do):
```
[...]

default        0

[...]

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-11-generic
[...]

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
[...]

title        Ubuntu 8.10, kernel 2.6.27-7-generic
[...]

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
[...]

title        Ubuntu 8.10, memtest86+
[...]

### END DEBIAN AUTOMAGIC KERNELS LIST

[...]

title        Windows Vista/Longhorn (loader)
[...]
```If I wanted to boot Windows by default I would find out what entry it is, I have 6 boot entries and Windows is the last one on the list so I would do 6 - 1 = 5 (GRUB starts at 0, so you have to subtract 1). Since Windows is the 5th entry, if I wanted it to be the default boot option I would change the line:
```
default        0
```
To:
```
default        5
```

---

### Post by Hobgoblin on 2009-03-22
Startup manager is the easiest way.  You can find it in add/remove programs

Make sure you select the Automatically update default boot option under the Advanced tab.

---

### Post by tanveerahmed2k8 on 2009-03-22
thanks for the help ppl

---

