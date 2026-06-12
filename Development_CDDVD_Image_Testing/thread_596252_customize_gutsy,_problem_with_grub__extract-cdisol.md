---
title: "customize gutsy, problem with grub : extract-cd/isolinux/isolinux.cfg"
date: 2007-10-29
forum: Development CD/DVD Image Testing
---

### Post by erwanj on 2007-10-29
Hi,

I am customizing a gutsy live cd and would like to make grub boot work with good locale, layout and keyboard parameters. I have to press F2 and F3 at the live cd boot in order to choose the boot parameters (lang and keyboard) and want to avoid users to do it.

I have seen that I can change extract-cd/isolinux/isolinux.cfg file. I have added these lines but I think that I don't need to add so much parameters (locale, preseed/locale, kbd-chooser/method, console-setup/layoutcode) and don't know which ones are not necessary. I don't know if I have to use the "fr_CH" or the "ch(fr)" form and don't find any information. 

```

LABEL livefr
  menu label Démarrer Ubuntu
  kernel /casper/vmlinuz
  append  locale=fr_CH preseed/locale=fr_CH kbd-chooser/method=ch(fr) console-setup/layoutcode=fr_CH file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL livede
  menu label Ubuntu starten
  kernel /casper/vmlinuz
  append  locale=de_CH preseed/locale=de_CH kbd-chooser/method=ch(de) console-setup/layoutcode=ch(de) file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL liveen
  menu label Start or install Ubuntu
  kernel /casper/vmlinuz
  append  locale=en preseed/locale=en kbd-chooser/method=en console-setup/layoutcode=en file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL liveit
  menu label Avvia o installa Ubuntu
  kernel /casper/vmlinuz
  append  locale=it preseed/locale=it kbd-chooser/method=it console-setup/layoutcode=it file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

```

Thank you.

Erwan

---

### Post by bdk6m2007 on 2008-02-08
Did you ever figure out which are the right parameters for what you're trying to do?  I'm trying something similar but haven't solved it yet.

---

