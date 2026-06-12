---
title: "One More Triple boot Question"
date: 2009-03-05
forum: General Help
---

### Post by wsonar on 2009-03-05
So now I'm on 8.10 got my GFXboot working good everything is grand

I got XP, Vista, and ubuntu installed in that order

I figure when I installed vista it replaced the ntloader with the new windowsloader

my question is can I boot directly to XP from my grub menu or do I have to go to the vista loader first?

I tried adding the XP as a seperate option in my menu.lst I'm sure I pointed it to the correct partitiono but it dosen't seem to work unless I use the vista loader

I assume because ntloader is not on the system anymore

Anybody got anything on this?

---

### Post by meierfra. on 2009-03-15
I assume that your main goal is to have  only one  boot menu.
This can by achieved fairly easily  by  adding  Ubuntu to the Vista Boot Menu with EasyBCD:

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

You should also edit menu.lst via "gksudo gedit /boot/grub/menu.lst"
and change "timemout 10"  to "timeout 2"  and "#hiddenmenu" to "hiddenmenu"



If you want I can also show you how to add XP to the Grub Menu, but that is more involved since one needs to separate the Vista and XP boot loaders.

---

### Post by wsonar on 2009-03-19
Yes I want them all on grub since I am using grub-gfxboot I want my cool themed gfxboot and to select ubuntu or xp or vista and go straight in

right now I choose

ubuntu 8.10        ________                     boots right into ubuntu

windows xp/vista    ________                    takes me to the windows bootloader for vista


my xp should be hd0,1

---

### Post by wsonar on 2009-03-19
title		Ubuntu Intrepid 8.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4dc07666-3182-4429-bee6-5c0a88bf1d9a ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
boot

#title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4dc07666-3182-4429-bee6-5c0a88bf1d9a ro single
#initrd		/boot/initrd.img-2.6.27-11-generic
#boot

#title		Debian GNU/Linux, kernel 2.6.24-23-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4dc07666-3182-4429-bee6-5c0a88bf1d9a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-23-generic
#boot

#title		Debian GNU/Linux, kernel 2.6.24-23-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4dc07666-3182-4429-bee6-5c0a88bf1d9a ro single
#initrd		/boot/initrd.img-2.6.24-23-generic
#boot

#title		Debian GNU/Linux, kernel memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin 
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Windows XP
#root            (hd0,1)
#makeactive
#chainloader	+     //?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP or Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra. on 2009-03-19
OK.  Here are the instruction:

[SIZE="3"][COLOR=blue] Boot into Vista[/COLOR][/SIZE]

** Step 1 Edit the Vista boot loader **

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Vista command line as  administrator. Type

```
  
bcdedit /set {bootmgr} device boot
bcdedit /set {bootmgr} timeout 0
bcdedit /delete {ntldr} /f

```



** Step 2 Fix the XP boot sector **

There are various ways to accomplish this. I will give you two options:

[COLOR="Red"]Option 1:[/COLOR]

Insert your Vista CD in the CDRom drive and wait for a few second. At the command line:


```

E:\boot\bootsect  /nt52 D: /force

```

Here "E" needs to be replaced by the drive letter of your CDrom drive and "D" by the drive letter of your XP partition. Just look in "Start->Computer" to determine the drive letters. Even if you know the drive letters, I suggest to double check. Vista and XP probably use different drive letters assignments. You need to use the drive letters used by Vista 

[COLOR="Red"]Option 2:[/COLOR]

Boot from your XP CD.
Press "r" to enter the repair console.
Use

```
map
```

to determine the drive letter of your XP partition. Type

```

fixboot C:

```

Here "C" needs to be replaced by the drive letter of your XP partition.

If neither Options 1 nor Option2 works for you, let me know and I can show you how to fix the boot sector from Ubuntu.


[SIZE="3"][COLOR=blue] Boot into Ubuntu.[/COLOR][/SIZE] 

Judging from your menu.lst I guess that XP is on /dev/sda1 and Vista is on /dev/sda2. But  you should double check (for example via "sudo fdisk -lu).  If this is no correct, let me know and I will adjust the instruction accordingly.

Open a terminal.

** Step 3 Add XP to "menu.lst" **

Open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```

Use the following for your XP and Vista entries

title XP
root (hd0,0)
chainloader +1

title Vista
root (hd0,1)
chainloader _1



** Step 4  Move the boot files from XP to Vista**



```
sudo mkdir /mnt/{XP,Vista}
sudo mount /dev/sda1 /mnt/XP
sudo mount /dev/sda2 /mnt/Vista
sudo mv /mnt/{XP,Vista}/bootmgr
sudo mv /mnt/{XP,Vista}/Boot

```
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/XP" the determine the correct spelling. 


That should be it. Reboot and see whether you can boot into all your OSs.
Let me know if you need additional help, or run into problems.

---

### Post by wsonar on 2009-03-19
Awesome worked like a charm, Thanks for all the help it's pretty cool now they all boot directly from grub

---

### Post by wsonar on 2009-03-19
Do I need to mark this as solved or will a mod do that? I did not see an option under the thread tools.

Thanks

---

### Post by meierfra. on 2009-03-19
> Awesome worked like a charm

Great.  Have fun with all your OSs.

> Do I need to mark this as solved or will a mod do that? I did not see an option under the thread tools.

Unfortunately the "Mark as Solved" feature was disable due to problems with the servers. Instead, just edit  the title of your first post so that it starts with  "[Solved]".

---

