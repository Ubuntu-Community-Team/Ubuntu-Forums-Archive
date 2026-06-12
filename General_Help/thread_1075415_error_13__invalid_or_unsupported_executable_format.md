---
title: "error 13 : invalid or unsupported executable format"
date: 2009-02-20
forum: General Help
---

### Post by achadual on 2009-02-20
Hello, I've tried searching for the same error but none of the answers worked for me.
I've had installed ubuntu and windows xp for about a year and never got an error. When I started my computer today and chose windows xp I got the "error 13 : invalid or unsupported executable format" so I run ubuntu and search on the internet for a solution. I tried modifying the menu.lst as I read in some posts but didn't work. I realized that windows didn't shut down properly, because when I try to mount the common partition I get this:
 
"$LogFile indicates unclean shutdown (0, 0) failed to mount '/dev/sda7' not supported operation. Mount is denied because NFTS is marked to be in use" then gives me some options to disconnect the device and more.


I checked fdisk:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xe911e911

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551        3766     9767520   83  Linux
/dev/sda3            3767        9729    47897797+   f  W95 Ext'd (LBA)
/dev/sda5            3767        3890      995998+  82  Linux swap / Solaris
/dev/sda6            3891        5106     9767488+  83  Linux
/dev/sda7            5107        9729    37134216    7  HPFS/NTFS


and also menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2c0a42a1-acdd-4e3b-8312-b4f32bb443e0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false




## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c0a42a1-acdd-4e3b-8312-b4f32bb443e0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c0a42a1-acdd-4e3b-8312-b4f32bb443e0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c0a42a1-acdd-4e3b-8312-b4f32bb443e0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c0a42a1-acdd-4e3b-8312-b4f32bb443e0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I tried (hd0,0), (hd0,1), (hd0,2), (hd1,0), (hd1,1). I don't know what else I can do, fdisk tells that sda1 is the right folder, and I had never modified the menu.lst until today, so I don't know what caused this crash.  

Thank you.

---

### Post by caljohnsmith on 2009-02-20
How about trying the following:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
Please post the output of all the above commands, and if they complete successfully, try booting Windows again (make sure to use (hd0,0) in your menu.lst) and let me know if that works or not.

---

### Post by achadual on 2009-02-21
acha@PORTATIL:~$ **sudo apt-get install ntfsprogs**
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libntfs10
Se instalarán los siguientes paquetes NUEVOS:
  libntfs10 ntfsprogs
0 actualizados, 2 se instalarán, 0 para eliminar y 133 no actualizados.
Necesito descargar 391kB de archivos.
Se utilizarán 950kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Des:1 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main libntfs10 2.0.0-1ubuntu2 [122kB]
Des:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main ntfsprogs 2.0.0-1ubuntu2 [269kB] 
Descargados 391kB en 9s (41,4kB/s)                                             
Seleccionando el paquete libntfs10 previamente no seleccionado.
(Leyendo la base de datos ...  
124346 ficheros y directorios instalados actualmente.)
Desempaquetando libntfs10 (de .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Seleccionando el paquete ntfsprogs previamente no seleccionado.
Desempaquetando ntfsprogs (de .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Configurando libntfs10 (2.0.0-1ubuntu2) ...

Configurando ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


acha@PORTATIL:~$ **sudo ntfsfix /dev/sda1**
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.


acha@PORTATIL:~$ **sudo mount /dev/sda1 /mnt && ls -l /mnt**
mount: debe especificar el tipo de sistema de ficheros
(you must specify the file system type)  ntfs??

I tried ntfsfix for sda7 (the common partition)
acha@PORTATIL:~$ **sudo ntfsfix /dev/sda7**
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda7 was processed successfully.

It worked, now I can access the common partition, but when I reboot and try to run windows it keeps saying  "error 13 : invalid or unsupported executable format"

---

### Post by caljohnsmith on 2009-02-21
OK, how about next booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show you the drive letters for all your partitions; find the drive letter for your main sda1 Windows partition (probably "C") and do:
```
chkdsk /r C:
```
And let me know what that command returns. If the command runs at all, run it as many times as it takes until it reports no errors. Let me know how that goes.

---

### Post by achadual on 2009-02-21
The problem is that I don´t have the windows install cd. Isn´t there anyway to enter the console before the grub menu comes up?

---

### Post by achadual on 2009-02-25
All right, I found a windows xp installation cd. I enter the BIOS and go to boot menu, place cd/dvd in first place but the cd doesn't load. I also tried accessing the boot menu and choosing cd/dvd boot but the GRUB pops up every time. 
I read some other posts and found out some guys that recommend disabling the HDD in the BIOS boot menu so it will surely boot from cd, I didn't find the way to do that.
I don't know what else to do..
Thank you.

---

