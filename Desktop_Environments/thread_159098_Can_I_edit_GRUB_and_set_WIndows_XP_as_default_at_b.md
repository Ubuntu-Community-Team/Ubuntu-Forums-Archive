---
title: "Can I edit GRUB and set WIndows XP as default at booting?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by dnccnd on 2006-04-12
Hallo!

I am a total beginner. I have installed Ubuntu 5.10 on a partition of my HD after having installed Windows XP on another partition. Everything works well.

By default, GRUB chooses Ubuntu. As I am still working mostly in Windows - and as my wife uses the PC as well and doesn't want to lose time to choose Windows at booting :( - I would like to change the settings of GRUB so that Windows becomes the default system.

Can anyone help me? Thanks in advance!

---

### Post by intangir1999 on 2006-04-12
I had always thought most Distro's have an Advanced Mode of Installation, I know when I installed Mandrake on my win2k machine a few years ago, I was able to tell it to boot up win2k by default.  I have tried doing this through the Control Pad (I think that's what it's called, its under the System menu), there is an option called Boot Menu, this portion should give you further information on switching the default OS.  However, be cautioned, the last time I tried doing the change after installation, GRUB did not recognize my other OS and would constantly boot up into Linux even when I would tell it not to.

---

### Post by mscman on 2006-04-12
Absolutely.  First thing you need to do is open a terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
Then you want to change the number of the default menu choice.  Scroll down until you see:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0
```
Change the '0' next to default to the number your XP choice is on your boot screen.  For example, if it is on the 5th line down, you would change it to
```
default     4
```
Since numbering starts at 0.  If you can't remember which line it is, scroll down until you see```
title           Ubuntu, kernel 2.6.15-20-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-20-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-20-386
savedefault
boot

```
or whatever you first Ubuntu kernel is, and count the number of paragraphs until you reach the XP partition.
Sorry if any of this is confusing...  I'm sure you will figure it out, but ask if you need any clarification...

---

### Post by mannheim on 2006-04-12
Edit the file /boot/grub/menu.lst, e.g. by using gedit, making a backup first:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```

The default installation procedure will have given you an entry for Windows XP in menu.lst somewhere towards the bottom of the file: it looks something like

```

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Cut 'n paste the corrsponding lines in your own menu.lst, moving them to the point in the menu.lst file just *above* the lines which look like:

```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

```

(These lines should also be in menu.lst following a default install.) Then reboot. If it all goes horribly wrong, you will need to boot from the live cd (or something else), and copy back your original menu.lst.

---

### Post by mannheim on 2006-04-12
[QUOTE=mscman]
Change the '0' next to default to the number your XP choice is on your boot screen.  For example, if it is on the 5th line down, you would change it to
```
default     4
```
[/QUOTE]

I hadn't tried this simpler method, because I thought that it might run into the following problem: if there is a kernel update, the automatic update of menu.lst will add the new kernel to the list of boot options, together with the old kernel. The result is that "Windows XP" is no further down the list, and we need to change "4" to "6" or whatever.

But thinking about it again, I wonder whether perhaps the automatic update of menu.lst is smart enough to take care of this -- changing 4 to 6 automatically in this scenario.

---

### Post by keen0300 on 2006-04-12
[QUOTE=mannheim]I hadn't tried this simpler method, because I thought that it might run into the following problem: if there is a kernel update, the automatic update of menu.lst will add the new kernel to the list of boot options, together with the old kernel. The result is that "Windows XP" is no further down the list, and we need to change "4" to "6" or whatever.

But thinking about it again, I wonder whether perhaps the automatic update of menu.lst is smart enough to take care of this -- changing 4 to 6 automatically in this scenario.[/QUOTE]

I've done the simpler method. Unfortunately the automatic update is not smart enough to to take care of the change. You do have to change your menu.lst when you make that kind of change.

---

### Post by dnccnd on 2006-04-12
Thank you all for your quick replies! You are all amazing! :-D 

I used mcsman suggestion and edited the menu.lst file. I had to type 6 because the separation line between the Ubuntu systems (or kernel?) and Windows is also counted.

Very easy and effective! \\:D/

---

### Post by mscman on 2006-04-12
> But thinking about it again, I wonder whether perhaps the automatic update of menu.lst is smart enough to take care of this -- changing 4 to 6 automatically in this scenario.

Actually, it isn't updated and will have to be changed manually.  The other thing to take into account is the fact that the 'divider' counts as a line.  For example:
starting from the top, there are 2 Ubuntu versions for a kernel (regular 0 and 'safe-mode' 1), a mem test (2), and XP(3), the default number has to be 4 because there is a divider.  Again, kind of confusing, but if you play with it a little, you'll figure it out.

---

### Post by dnccnd on 2006-04-12
when I typed the following in Terminal as suggested by mscman:

sudo gedit /boot/grub/menu.lst

the menu.lts file opened and I just had to edit the number and save the file.

then everything worked at the first reboot...

---

### Post by mscman on 2006-04-12
[QUOTE=dnccnd]when I typed the following in Terminal as suggested by mscman:

sudo gedit /boot/grub/menu.lst

the menu.lts file opened and I just had to edit the number and save the file.

then everything worked at the first reboot...[/QUOTE]
Glad to hear that!  Hope your Ubuntu experience is as great as mine has been!:grin:

---

### Post by kevieboy on 2006-04-12
Just wondering...If you screw up and type the wrong number, will you still be able to boot into ubuntu to change it?

---

### Post by Ramses de Norre on 2006-04-12
Yes, you only change which OS is loaded if you don't make a choice. So you can always make a choice and press enter before the default gets loaded.

---

### Post by aysiu on 2006-04-12
[QUOTE=Ramses de Norre]Yes, you only change which OS is loaded if you don't make a choice. So you can always make a choice and press enter before the default gets loaded.[/QUOTE] Just don't change the timeout to 0.

---

