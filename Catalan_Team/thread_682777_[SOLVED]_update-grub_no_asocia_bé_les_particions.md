---
title: "[SOLVED] update-grub no asocia bé les particions"
date: 2008-01-30
forum: Catalan Team
---

### Post by guillemsola on 2008-01-30
Sembla que desprès de botar amb un live-cd dela wifislax el meu grub s'he n'ha anat a pps.

El cas és que fent un update-grub busca els kernels del meu ubuntu i els associa a (hd0,7) però això provoca un error al grub, no ho pot muntar. Ho edito manualment per (hd0,6) i funciona correctament.

Per les copies de seguretat del menu.lst del grub que tinc el meu ubuntu semprè havia estat a hd0,7 és la /dev/sda7 però desprès d'aquest incident perquè el grub trobi l'ubuntu ha d'estar a hd0,6 ja que l'update-grub l'assigna a hd0,7 i aleshores el grub no troba la partició.

Us llisto el resultat de fdisk -l. 
> 
Disc /dev/sda: 100.0 GiB, 100030242816 octets
255 capçals, 63 sectors/pista, 12161 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sda1               1         243     1951866   1b  W95 FAT32 oculta
/dev/sda2   *         244        7402    57504667+   7  HPFS/NTFS
/dev/sda3            7403       12161    38226667+   f  W95 estesa (LBA)
/dev/sda5            7403        9576    17462623+   7  HPFS/NTFS
/dev/sda6            9577       10874    10426153+  83  Linux
/dev/sda7           10875       12023     9229311   83  Linux
/dev/sda8           12024       12161     1108453+  82  Linux swap / Solaris
 

A la sda7 és on hi tinc el ubuntu i perquè arrenqui a de ser el (hd0,6), però l'update-grub insisteix a seleccionar (hd0,7). Afegirè que tinc una imatge bootsplash que fins que no he modificat al grub que es troba a (hd6,0) no podia carregar.

Tinc un sabayon linux a sda6 que surt al grub com a (hd0,5) i bota perfectament.

Alguna idea del que ha passat o com corretgir això?

Aquí enganxo el menu.lst del grub per si fes falta.

Gràcies!!

> 
default         6

timeout         10

color cyan/blue white/blue

## ## End Default Options ##

splashimage=(hd0,6)/boot/grub/splash.xpm.gz

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e0dadc5a-e2be-4fb9-8b84-b2d271733b9e ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e0dadc5a-e2be-4fb9-8b84-b2d271733b9e ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e0dadc5a-e2be-4fb9-8b84-b2d271733b9e ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e0dadc5a-e2be-4fb9-8b84-b2d271733b9e ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Sabayon Linux x86 3.26 (on /dev/sda6)
root            (hd0,5)
kernel          /boot/kernel-genkernel-x86-2.6.19-gentoo-r4 root=/dev/ram0 ramdisk=8192 real_root=/dev/sda6 quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi 
initrd          /boot/initramfs-genkernel-x86-2.6.19-gentoo-r4
savedefault
boot



---

### Post by papapep on 2008-01-30
> Alguna idea del que ha passat o com corretgir això?


No acabo d'entendre  ben bé l'objecte del teu post. M'explico: no sé si és que no saps com resoldre el tema per a que t'arrenqui bé el sistema, o si planteges com fer funcionar correctament l'update-grub.

Si el cas és el primer, doncs símplement modifica el menu.lst amb els valors correctes. Si és el segon, ni la més remota idea.

El que jo faria també és verificar que les UUID's que surt al menu.lst sigui el correcte. Si en un terminal fas:

```
ls -l /dev/disk/by-uuid
```

veuràs les UUID's que tenen assignades les particions, i la podràs comparar amb les que tens dins del menu.lst.

Espero haver-te entès correctament.

---

### Post by guillemsola on 2008-02-01
gràcies per l'interes, la cosa a anat a més, vull dir que al final trastejant trastejant per tal de que el grub reconegués la partició amb l'ubuntu m'he carregat la partició amb el aka:software propietari.

La dona em volia matar pq ella és la que fa servir l'innombrable. 	

Per sort per aquest desastres he tret el **Hiren's boot CD** de l'estanteria *[http://es.wikipedia.org/wiki/Hiren's_boot_CD](http://es.wikipedia.org/wiki/Hiren's_boot_CD)* i amb una utilitat que es diu *Partition Table Doctor 3.5* he resucitat la partició de Redmon. Oli en un llum

Després d'haver perdut el grub. He seguit els passos de la guia ubuntu *[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)* i ja torno a tenir el grub funcionant correctament. Aquests passos per recuperar el grub ja els havia fet abans sense éxit pero ara tot va perfecte.

Ja estic salvat. Això si, després d'haver escoltat unes quantes pestes sobre el linux! \\:D/

Salut

---

