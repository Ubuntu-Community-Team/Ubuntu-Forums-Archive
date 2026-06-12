---
title: "Problem acessing another partitions"
date: 2008-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jamaj on 2008-07-29
Since today afternoon, when the system made an upgrade, some strange things became happening with my Dell Inspiron 1525.

1) All windows partitions cannot be mounted anymore. I installed Ubuntu 8.04 in a partion and the Windows Vista partition prior was accessible. Not anymore: when i click on OS, RECOVERY icons, i receive a message: Fuse: cannot mount. Resource is busy. But i am in Ubuntu!!

2) The first time i rebooted after upgrade, the screen showed a lot of line segments. The second reboot, it became ok

3) Now i have two kernels: the first and the second one. What can i do to revert. Things were to good before...


Thanks in advance

Jamaj

---

### Post by gbrainin on 2008-07-29
To use the older kernel, just scroll down (use the down-arrow button) when the menu is up.  Then hit enter to select the kernel you want.

---

### Post by jamaj on 2008-07-29
With all versions the mess is the same.

I cannot access windows partitons anymore. But when i boot from ubuntu cd, I can see all windows partitions normally.
I thought Ubuntu was a stable system. But a simple update can cause this...

Is there any command, like the one used by instalation Ubuntu CD to discover and recognize all partitions, that could repair my system?

Fuse: mount failed devices or resources busy



Thanks in advance

---

### Post by jamaj on 2008-07-29
Something really strange is occurring. 
When i boot by CD, and type 

sudo fdisk -l, it recogmnizes everything ok. and i can acccess all partitions, windows and linux, ok.

But when i boot normally, by HD, the sudo fdisk -l gives a lot of erros:

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8000000

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1               1           9       72261   de  Utilitário Dell
/dev/sda2              10        1315    10485760    7  HPFS ou NTFS
/dev/sda3   *        1315        5874    36621094    7  HPFS ou NTFS
/dev/sda4            5875       14594    70036392+   f  Win95 (LBA) Partição Extendida
/dev/sda5           14267       14594     2620416   dd  Desconhecido
/dev/sda6            5875       13919    64621431   83  Linux
/dev/sda7           13920       14266     2787246   82  Linux swap / Solaris

Partições lógicas fora da ordem do disco

Disco /dev/dm-0: 73 MB, 73995264 bytes
255 heads, 63 sectors/track, 8 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a42b4c3

Isto não parece ser uma tabela de partições
Provavelmente você selecionou o dispositivo errado.

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/dm-0p1            1880      111816   883058677+  cd  Desconhecido
A partição 1 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (0, 190, 62) lógico = (1879, 146, 63)
A partição 1 possui fins físico/lógico diferentes:
     fís. = (257, 19, 50) lógico = (111815, 75, 50)
A partição 1 não termina no limite do cilindro.
/dev/dm-0p2   ?       33873      138704   842053558   72  Desconhecido
A partição 2 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (101, 107, 32) lógico = (33872, 185, 42)
A partição 2 possui fins físico/lógico diferentes:
     fís. = (370, 114, 47) lógico = (138703, 139, 40)
A partição 2 não termina no limite do cilindro.
/dev/dm-0p3   ?       69058       69060       10020+  45  Desconhecido
A partição 3 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (68, 114, 0) lógico = (69057, 206, 23)
A partição 3 possui fins físico/lógico diferentes:
     fís. = (322, 76, 12) lógico = (69059, 14, 29)
A partição 3 não termina no limite do cilindro.

Disco /dev/dm-1: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

Isto não parece ser uma tabela de partições
Provavelmente você selecionou o dispositivo errado.

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/dm-1p1   ?         410      119791   958924038+  70  Multi-Boot DiskSecure
A partição 1 não termina no limite do cilindro.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Desconhecido
A partição 2 não termina no limite do cilindro.
/dev/dm-1p3   ?       14052       14052           5   72  Desconhecido
A partição 3 não termina no limite do cilindro.
/dev/dm-1p4          164483      164486       25945    0  Vazia
A partição 4 não termina no limite do cilindro.

Partições lógicas fora da ordem do disco

Disco /dev/dm-2: 37.5 GB, 37500000256 bytes
255 heads, 63 sectors/track, 4559 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

Isto não parece ser uma tabela de partições
Provavelmente você selecionou o dispositivo errado.

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/dm-2p1   ?         410      119791   958924038+  70  Multi-Boot DiskSecure
A partição 1 não termina no limite do cilindro.
/dev/dm-2p2   ?      121585      234786   909287957+  43  Desconhecido
A partição 2 não termina no limite do cilindro.
/dev/dm-2p3   ?       14052       14052           5   72  Desconhecido
A partição 3 não termina no limite do cilindro.
/dev/dm-2p4          164483      164486       25945    0  Vazia
A partição 4 não termina no limite do cilindro.

Partições lógicas fora da ordem do disco

Disco /dev/dm-3: 2683 MB, 2683305984 bytes
255 heads, 63 sectors/track, 326 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

Isto não parece ser uma tabela de partições
Provavelmente você selecionou o dispositivo errado.

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/dm-3p1   ?       48437      119493   570754815+  72  Desconhecido
A partição 1 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (357, 116, 40) lógico = (48436, 183, 40)
A partição 1 possui fins físico/lógico diferentes:
     fís. = (357, 32, 45) lógico = (119492, 104, 7)
A partição 1 não termina no limite do cilindro.
/dev/dm-3p2   ?       10501      131013   968014120   65  Novell Netware 386
A partição 2 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (288, 115, 43) lógico = (10500, 111, 30)
A partição 2 possui fins físico/lógico diferentes:
     fís. = (367, 114, 50) lógico = (131012, 158, 28)
A partição 2 não termina no limite do cilindro.
/dev/dm-3p3   ?      116395      236907   968014096   79  Desconhecido
A partição 3 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (366, 32, 33) lógico = (116394, 188, 12)
A partição 3 possui fins físico/lógico diferentes:
     fís. = (357, 32, 43) lógico = (236906, 234, 25)
A partição 3 não termina no limite do cilindro.
/dev/dm-3p4   ?      179626      179629       27749+   d  Desconhecido
A partição 4 possui inícios físico/lógico diferentes (não Linux?):
     fís. = (372, 97, 50) lógico = (179625, 87, 47)
A partição 4 possui fins físico/lógico diferentes:
     fís. = (0, 10, 0) lógico = (179628, 203, 42)
A partição 4 não termina no limite do cilindro.

Partições lógicas fora da ordem do disco

---

### Post by jamaj on 2008-07-29
Please people, help me. 
What should i do to make Ubuntu behave like if it was booted from CD, recognizing all partitions right?

---

