---
title: "Deleted Files Vanishing"
date: 2009-03-14
forum: Desktop Environments
---

### Post by suffer1989 on 2009-03-14
I had a directory full of Pictures i imported from a digicam. However, I tried to delete them but, permission was denied. So I decided t act smart, and i used Sudo nautilus and deleted the files from there. However, the only option i got was "move to trash". I clicked that, and the folder vanished. However, the space is still being occupied (3.2GBs). I checked in the trash, and its not there . Can anyone Help me ?

---

### Post by mtbsoft on 2009-03-14
My only thoughts are... were you still using the sudo nautilus when you checked the trash bin?  If not it may be that you can't see them in there and need to use sudo nautilus again to view and clear the trash.  Other than that I'm at a loss... perhaps a disk check might find the missing space?

---

### Post by suffer1989 on 2009-03-14
I tired looking at the trash, but all i got was :

Sorry, could not display all the contents of "trash": Operation not supported

????

---

### Post by ajgreeny on 2009-03-14
It should all be in root's trash, so look for /.Trash using gksudo nautilus and you can then delete the files properly or restore them.  On my machine with hardy it's called /.Trash-1000, and it appears at the top of the output of the command ```
locate -i trash
```

---

### Post by suffer1989 on 2009-03-14
> **ajgreeny said:**
> It should all be in root's trash, so look for /.Trash using gksudo nautilus and you can then delete the files properly or restore them.  On my machine with hardy it's called /.Trash-1000, and it appears at the top of the output of the command ```
locate -i trash
```


All I get is this :

```
sufy@sufy-laptop:~$ locate -i trash
/home/sufy/.gconf/apps/panel/applets/trashapplet_screen0
/home/sufy/.gconf/apps/panel/applets/trashapplet_screen0/%gconf.xml
/home/sufy/.kde/share/apps/kmail/mail/.trash.index
/home/sufy/.kde/share/apps/kmail/mail/.trash.index.ids
/home/sufy/.kde/share/apps/kmail/mail/trash
/home/sufy/.kde/share/apps/kmail/mail/trash/cur
/home/sufy/.kde/share/apps/kmail/mail/trash/new
/home/sufy/.kde/share/apps/kmail/mail/trash/tmp
/home/sufy/.local/share/Trash
/home/sufy/.local/share/Trash/files
/home/sufy/.local/share/Trash/info
/home/sufy/.local/share/Trash/info/interfaces.trashinfo
/home/sufy/.local/share/Trash/info/vbox.cfg.trashinfo
/home/sufy/ffmpeg/tools/trasher.c
/home/sufy/ffmpeg/tools/.svn/text-base/trasher.c.svn-base
/root/.local/share/Trash
/usr/bin/gvfs-trash
/usr/bin/ktrash
/usr/lib/bonobo/servers/GNOME_Panel_TrashApplet.server
/usr/lib/gnome-applets/trashapplet
/usr/lib/gvfs/gvfsd-trash
/usr/lib/kde4/kio_trash.so
/usr/lib/kde4/plasma_applet_trash.so
/usr/share/gnome/help/trashapplet
/usr/share/gnome/help/trashapplet/C
/usr/share/gnome/help/trashapplet/ca
/usr/share/gnome/help/trashapplet/da
/usr/share/gnome/help/trashapplet/de
/usr/share/gnome/help/trashapplet/el
/usr/share/gnome/help/trashapplet/en_GB
/usr/share/gnome/help/trashapplet/es
/usr/share/gnome/help/trashapplet/fi
/usr/share/gnome/help/trashapplet/fr
/usr/share/gnome/help/trashapplet/hu
/usr/share/gnome/help/trashapplet/it
/usr/share/gnome/help/trashapplet/nl
/usr/share/gnome/help/trashapplet/oc
/usr/share/gnome/help/trashapplet/pa
/usr/share/gnome/help/trashapplet/pt_BR
/usr/share/gnome/help/trashapplet/ru
/usr/share/gnome/help/trashapplet/sv
/usr/share/gnome/help/trashapplet/uk
/usr/share/gnome/help/trashapplet/zh_HK
/usr/share/gnome/help/trashapplet/zh_TW
/usr/share/gnome/help/trashapplet/C/figures
/usr/share/gnome/help/trashapplet/C/legal.xml
/usr/share/gnome/help/trashapplet/C/trashapplet.xml
/usr/share/gnome/help/trashapplet/C/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/ca/figures
/usr/share/gnome/help/trashapplet/ca/trashapplet.xml
/usr/share/gnome/help/trashapplet/ca/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/da/figures
/usr/share/gnome/help/trashapplet/da/trashapplet.xml
/usr/share/gnome/help/trashapplet/da/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/de/figures
/usr/share/gnome/help/trashapplet/de/trashapplet.xml
/usr/share/gnome/help/trashapplet/de/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/el/figures
/usr/share/gnome/help/trashapplet/el/trashapplet.xml
/usr/share/gnome/help/trashapplet/el/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/en_GB/figures
/usr/share/gnome/help/trashapplet/en_GB/trashapplet.xml
/usr/share/gnome/help/trashapplet/en_GB/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/es/figures
/usr/share/gnome/help/trashapplet/es/trashapplet.xml
/usr/share/gnome/help/trashapplet/es/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/fi/figures
/usr/share/gnome/help/trashapplet/fi/trashapplet.xml
/usr/share/gnome/help/trashapplet/fi/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/fr/figures
/usr/share/gnome/help/trashapplet/fr/trashapplet.xml
/usr/share/gnome/help/trashapplet/fr/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/hu/figures
/usr/share/gnome/help/trashapplet/hu/trashapplet.xml
/usr/share/gnome/help/trashapplet/hu/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/it/figures
/usr/share/gnome/help/trashapplet/it/trashapplet.xml
/usr/share/gnome/help/trashapplet/it/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/nl/figures
/usr/share/gnome/help/trashapplet/nl/trashapplet.xml
/usr/share/gnome/help/trashapplet/nl/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/oc/figures
/usr/share/gnome/help/trashapplet/oc/trashapplet.xml
/usr/share/gnome/help/trashapplet/oc/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/pa/figures
/usr/share/gnome/help/trashapplet/pa/trashapplet.xml
/usr/share/gnome/help/trashapplet/pa/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/pt_BR/figures
/usr/share/gnome/help/trashapplet/pt_BR/trashapplet.xml
/usr/share/gnome/help/trashapplet/pt_BR/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/ru/figures
/usr/share/gnome/help/trashapplet/ru/trashapplet.xml
/usr/share/gnome/help/trashapplet/ru/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/sv/figures
/usr/share/gnome/help/trashapplet/sv/trashapplet.xml
/usr/share/gnome/help/trashapplet/sv/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/uk/figures
/usr/share/gnome/help/trashapplet/uk/trashapplet.xml
/usr/share/gnome/help/trashapplet/uk/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/zh_HK/figures
/usr/share/gnome/help/trashapplet/zh_HK/trashapplet.xml
/usr/share/gnome/help/trashapplet/zh_HK/figures/trash-applet.png
/usr/share/gnome/help/trashapplet/zh_TW/figures
/usr/share/gnome/help/trashapplet/zh_TW/trashapplet.xml
/usr/share/gnome/help/trashapplet/zh_TW/figures/trash-applet.png
/usr/share/gnome/help/user-guide/C/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/ar/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/bg/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/de/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/el/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/es/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/fi/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/fr/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/hu/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/it/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/ja/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/ko/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/oc/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/pa/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/pt/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/pt_BR/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/ru/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/sv/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/th/figures/naut_trash_launcher.png
/usr/share/gnome/help/user-guide/zh_CN/figures/naut_trash_launcher.png
/usr/share/gnome-2.0/ui/GNOME_Panel_TrashApplet.xml
/usr/share/gnome-applets/builder/trashapplet-empty-progress.ui
/usr/share/gvfs/mounts/trash.mount
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/emptytrash.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/gnome-fs-trash-empty.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/gnome-stock-trash.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/trashcan_empty.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/user-trash.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/places/xfce-trash_empty.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/edittrash.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/gnome-fs-trash-full.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/gnome-stock-trash-full.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/stock_trash_full.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/trashcan_full.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/user-trash-full.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/status/xfce-trash_full.png
/usr/share/icons/Human/16x16/places/emptytrash.png
/usr/share/icons/Human/16x16/places/gnome-fs-trash-empty.png
/usr/share/icons/Human/16x16/places/gnome-stock-trash.png
/usr/share/icons/Human/16x16/places/trashcan_empty.png
/usr/share/icons/Human/16x16/places/user-trash.png
/usr/share/icons/Human/16x16/places/xfce-trash_empty.png
/usr/share/icons/Human/16x16/status/edittrash.png
/usr/share/icons/Human/16x16/status/gnome-fs-trash-full.png
/usr/share/icons/Human/16x16/status/gnome-stock-trash-full.png
/usr/share/icons/Human/16x16/status/stock_trash_full.png
/usr/share/icons/Human/16x16/status/trashcan_full.png
/usr/share/icons/Human/16x16/status/user-trash-full.png
/usr/share/icons/Human/16x16/status/xfce-trash_full.png
/usr/share/icons/Human/22x22/places/emptytrash.png
/usr/share/icons/Human/22x22/places/gnome-fs-trash-empty.png
/usr/share/icons/Human/22x22/places/gnome-stock-trash.png
/usr/share/icons/Human/22x22/places/trashcan_empty.png
/usr/share/icons/Human/22x22/places/user-trash.png
/usr/share/icons/Human/22x22/places/xfce-trash_empty.png
/usr/share/icons/Human/22x22/status/edittrash.png
/usr/share/icons/Human/22x22/status/gnome-fs-trash-full.png
/usr/share/icons/Human/22x22/status/gnome-stock-trash-full.png
/usr/share/icons/Human/22x22/status/stock_trash_full.png
/usr/share/icons/Human/22x22/status/trashcan_full.png
/usr/share/icons/Human/22x22/status/user-trash-full.png
/usr/share/icons/Human/22x22/status/xfce-trash_full.png
/usr/share/icons/Human/24x24/places/emptytrash.png
/usr/share/icons/Human/24x24/places/gnome-fs-trash-empty.png
/usr/share/icons/Human/24x24/places/gnome-stock-trash.png
/usr/share/icons/Human/24x24/places/trashcan_empty.png
/usr/share/icons/Human/24x24/places/user-trash.png
/usr/share/icons/Human/24x24/places/xfce-trash_empty.png
/usr/share/icons/Human/24x24/status/edittrash.png
/usr/share/icons/Human/24x24/status/gnome-fs-trash-full.png
/usr/share/icons/Human/24x24/status/gnome-stock-trash-full.png
/usr/share/icons/Human/24x24/status/stock_trash_full.png
/usr/share/icons/Human/24x24/status/trashcan_full.png
/usr/share/icons/Human/24x24/status/user-trash-full.png
/usr/share/icons/Human/24x24/status/xfce-trash_full.png
/usr/share/icons/Human/48x48/places/emptytrash.png
/usr/share/icons/Human/48x48/places/gnome-fs-trash-empty.png
/usr/share/icons/Human/48x48/places/gnome-stock-trash.png
/usr/share/icons/Human/48x48/places/trashcan_empty.png
/usr/share/icons/Human/48x48/places/user-trash.png
/usr/share/icons/Human/48x48/places/xfce-trash_empty.png
/usr/share/icons/Human/48x48/status/edittrash.png
/usr/share/icons/Human/48x48/status/gnome-fs-trash-full.png
/usr/share/icons/Human/48x48/status/gnome-stock-trash-full.png
/usr/share/icons/Human/48x48/status/stock_trash_full.png
/usr/share/icons/Human/48x48/status/trashcan_full.png
/usr/share/icons/Human/48x48/status/user-trash-full.png
/usr/share/icons/Human/48x48/status/xfce-trash_full.png
/usr/share/icons/Human/scalable/places/emptytrash.svg
/usr/share/icons/Human/scalable/places/gnome-fs-trash-empty.svg
/usr/share/icons/Human/scalable/places/gnome-stock-trash.svg
/usr/share/icons/Human/scalable/places/trashcan_empty.svg
/usr/share/icons/Human/scalable/places/user-trash.svg
/usr/share/icons/Human/scalable/places/xfce-trash_empty.svg
/usr/share/icons/Human/scalable/status/edittrash.svg
/usr/share/icons/Human/scalable/status/gnome-fs-trash-full.svg
/usr/share/icons/Human/scalable/status/gnome-stock-trash-full.svg
/usr/share/icons/Human/scalable/status/stock_trash_full.svg
/usr/share/icons/Human/scalable/status/trashcan_full.svg
/usr/share/icons/Human/scalable/status/user-trash-full.svg
/usr/share/icons/Human/scalable/status/xfce-trash_full.svg
/usr/share/icons/Tangerine/16x16/places/emptytrash.png
/usr/share/icons/Tangerine/16x16/places/gnome-fs-trash-empty.png
/usr/share/icons/Tangerine/16x16/places/gnome-stock-trash.png
/usr/share/icons/Tangerine/16x16/places/trashcan_empty.png
/usr/share/icons/Tangerine/16x16/places/user-trash.png
/usr/share/icons/Tangerine/16x16/places/xfce-trash_empty.png
/usr/share/icons/Tangerine/16x16/status/edittrash.png
/usr/share/icons/Tangerine/16x16/status/gnome-fs-trash-full.png
/usr/share/icons/Tangerine/16x16/status/gnome-stock-trash-full.png
/usr/share/icons/Tangerine/16x16/status/stock_trash_full.png
/usr/share/icons/Tangerine/16x16/status/trashcan_full.png
/usr/share/icons/Tangerine/16x16/status/user-trash-full.png
/usr/share/icons/Tangerine/16x16/status/xfce-trash_full.png
/usr/share/icons/Tangerine/22x22/places/emptytrash.png
/usr/share/icons/Tangerine/22x22/places/gnome-fs-trash-empty.png
/usr/share/icons/Tangerine/22x22/places/gnome-stock-trash.png
/usr/share/icons/Tangerine/22x22/places/trashcan_empty.png
/usr/share/icons/Tangerine/22x22/places/user-trash.png
/usr/share/icons/Tangerine/22x22/places/xfce-trash_empty.png
/usr/share/icons/Tangerine/22x22/status/edittrash.png
/usr/share/icons/Tangerine/22x22/status/gnome-fs-trash-full.png
/usr/share/icons/Tangerine/22x22/status/gnome-stock-trash-full.png
/usr/share/icons/Tangerine/22x22/status/stock_trash_full.png
/usr/share/icons/Tangerine/22x22/status/trashcan_full.png
/usr/share/icons/Tangerine/22x22/status/user-trash-full.png
/usr/share/icons/Tangerine/22x22/status/xfce-trash_full.png
/usr/share/icons/Tangerine/24x24/places/emptytrash.png
/usr/share/icons/Tangerine/24x24/places/gnome-fs-trash-empty.png
/usr/share/icons/Tangerine/24x24/places/gnome-stock-trash.png
/usr/share/icons/Tangerine/24x24/places/trashcan_empty.png
/usr/share/icons/Tangerine/24x24/places/user-trash.png
/usr/share/icons/Tangerine/24x24/places/xfce-trash_empty.png
/usr/share/icons/Tangerine/24x24/status/edittrash.png
/usr/share/icons/Tangerine/24x24/status/gnome-fs-trash-full.png
/usr/share/icons/Tangerine/24x24/status/gnome-stock-trash-full.png
/usr/share/icons/Tangerine/24x24/status/stock_trash_full.png
/usr/share/icons/Tangerine/24x24/status/trashcan_full.png
/usr/share/icons/Tangerine/24x24/status/user-trash-full.png
/usr/share/icons/Tangerine/24x24/status/xfce-trash_full.png
/usr/share/icons/Tangerine/32x32/places/emptytrash.png
/usr/share/icons/Tangerine/32x32/places/gnome-fs-trash-empty.png
/usr/share/icons/Tangerine/32x32/places/gnome-stock-trash.png
/usr/share/icons/Tangerine/32x32/places/trashcan_empty.png
/usr/share/icons/Tangerine/32x32/places/user-trash.png
/usr/share/icons/Tangerine/32x32/places/xfce-trash_empty.png
/usr/share/icons/Tangerine/32x32/status/edittrash.png
/usr/share/icons/Tangerine/32x32/status/gnome-fs-trash-full.png
/usr/share/icons/Tangerine/32x32/status/gnome-stock-trash-full.png
/usr/share/icons/Tangerine/32x32/status/stock_trash_full.png
/usr/share/icons/Tangerine/32x32/status/trashcan_full.png
/usr/share/icons/Tangerine/32x32/status/user-trash-full.png
/usr/share/icons/Tangerine/32x32/status/xfce-trash_full.png
/usr/share/icons/Tangerine/scalable/places/emptytrash.svg
/usr/share/icons/Tangerine/scalable/places/gnome-fs-trash-empty.svg
/usr/share/icons/Tangerine/scalable/places/gnome-stock-trash.svg
/usr/share/icons/Tangerine/scalable/places/trashcan_empty.svg
/usr/share/icons/Tangerine/scalable/places/user-trash.svg
/usr/share/icons/Tangerine/scalable/places/xfce-trash_empty.svg
/usr/share/icons/Tangerine/scalable/status/edittrash.svg
/usr/share/icons/Tangerine/scalable/status/gnome-fs-trash-full.svg
/usr/share/icons/Tangerine/scalable/status/gnome-stock-trash-full.svg
/usr/share/icons/Tangerine/scalable/status/stock_trash_full.svg
/usr/share/icons/Tangerine/scalable/status/trashcan_full.svg
/usr/share/icons/Tangerine/scalable/status/user-trash-full.svg
/usr/share/icons/Tangerine/scalable/status/xfce-trash_full.svg
/usr/share/icons/crystalsvg/128x128/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/128x128/filesystems/trashcan_full.png
/usr/share/icons/crystalsvg/16x16/actions/edittrash.png
/usr/share/icons/crystalsvg/16x16/actions/emptytrash.png
/usr/share/icons/crystalsvg/16x16/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/16x16/filesystems/trashcan_full.png
/usr/share/icons/crystalsvg/22x22/actions/edittrash.png
/usr/share/icons/crystalsvg/22x22/actions/emptytrash.png
/usr/share/icons/crystalsvg/22x22/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/22x22/filesystems/trashcan_full.png
/usr/share/icons/crystalsvg/32x32/actions/edittrash.png
/usr/share/icons/crystalsvg/32x32/actions/emptytrash.png
/usr/share/icons/crystalsvg/32x32/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/32x32/filesystems/trashcan_full.png
/usr/share/icons/crystalsvg/48x48/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/48x48/filesystems/trashcan_full.png
/usr/share/icons/crystalsvg/64x64/filesystems/trashcan_empty.png
/usr/share/icons/crystalsvg/64x64/filesystems/trashcan_full.png
/usr/share/icons/gnome/16x16/places/emptytrash.png
/usr/share/icons/gnome/16x16/places/gnome-fs-trash-empty.png
/usr/share/icons/gnome/16x16/places/gnome-stock-trash.png
/usr/share/icons/gnome/16x16/places/trashcan_empty.png
/usr/share/icons/gnome/16x16/places/user-trash.png
/usr/share/icons/gnome/16x16/places/xfce-trash_empty.png
/usr/share/icons/gnome/16x16/status/edittrash.png
/usr/share/icons/gnome/16x16/status/gnome-fs-trash-full.png
/usr/share/icons/gnome/16x16/status/gnome-stock-trash-full.png
/usr/share/icons/gnome/16x16/status/stock_trash_full.png
/usr/share/icons/gnome/16x16/status/trashcan_full.png
/usr/share/icons/gnome/16x16/status/user-trash-full.png
/usr/share/icons/gnome/16x16/status/xfce-trash_full.png
/usr/share/icons/gnome/16x16/stock/generic/stock_trash_full.png
/usr/share/icons/gnome/22x22/places/emptytrash.png
/usr/share/icons/gnome/22x22/places/gnome-fs-trash-empty.png
/usr/share/icons/gnome/22x22/places/gnome-stock-trash.png
/usr/share/icons/gnome/22x22/places/trashcan_empty.png
/usr/share/icons/gnome/22x22/places/user-trash.png
/usr/share/icons/gnome/22x22/places/xfce-trash_empty.png
/usr/share/icons/gnome/22x22/status/edittrash.png
/usr/share/icons/gnome/22x22/status/gnome-fs-trash-full.png
/usr/share/icons/gnome/22x22/status/gnome-stock-trash-full.png
/usr/share/icons/gnome/22x22/status/stock_trash_full.png
/usr/share/icons/gnome/22x22/status/trashcan_full.png
/usr/share/icons/gnome/22x22/status/user-trash-full.png
/usr/share/icons/gnome/22x22/status/xfce-trash_full.png
/usr/share/icons/gnome/24x24/places/emptytrash.png
/usr/share/icons/gnome/24x24/places/gnome-fs-trash-empty.png
/usr/share/icons/gnome/24x24/places/gnome-stock-trash.png
/usr/share/icons/gnome/24x24/places/trashcan_empty.png
/usr/share/icons/gnome/24x24/places/user-trash.png
/usr/share/icons/gnome/24x24/places/xfce-trash_empty.png
/usr/share/icons/gnome/24x24/status/edittrash.png
/usr/share/icons/gnome/24x24/status/gnome-fs-trash-full.png
/usr/share/icons/gnome/24x24/status/gnome-stock-trash-full.png
/usr/share/icons/gnome/24x24/status/stock_trash_full.png
/usr/share/icons/gnome/24x24/status/trashcan_full.png
/usr/share/icons/gnome/24x24/status/user-trash-full.png
/usr/share/icons/gnome/24x24/status/xfce-trash_full.png
/usr/share/icons/gnome/24x24/stock/generic/stock_trash_full.png
/usr/share/icons/gnome/32x32/places/emptytrash.png
/usr/share/icons/gnome/32x32/places/gnome-fs-trash-empty.png
/usr/share/icons/gnome/32x32/places/gnome-stock-trash.png
/usr/share/icons/gnome/32x32/places/trashcan_empty.png
/usr/share/icons/gnome/32x32/places/user-trash.png
/usr/share/icons/gnome/32x32/places/xfce-trash_empty.png
/usr/share/icons/gnome/32x32/status/edittrash.png
/usr/share/icons/gnome/32x32/status/gnome-fs-trash-full.png
/usr/share/icons/gnome/32x32/status/gnome-stock-trash-full.png
/usr/share/icons/gnome/32x32/status/stock_trash_full.png
/usr/share/icons/gnome/32x32/status/trashcan_full.png
/usr/share/icons/gnome/32x32/status/user-trash-full.png
/usr/share/icons/gnome/32x32/status/xfce-trash_full.png
/usr/share/icons/gnome/scalable/places/emptytrash.svg
/usr/share/icons/gnome/scalable/places/gnome-fs-trash-empty.svg
/usr/share/icons/gnome/scalable/places/gnome-stock-trash.svg
/usr/share/icons/gnome/scalable/places/trashcan_empty.svg
/usr/share/icons/gnome/scalable/places/user-trash.svg
/usr/share/icons/gnome/scalable/places/xfce-trash_empty.svg
/usr/share/icons/gnome/scalable/status/edittrash.svg
/usr/share/icons/gnome/scalable/status/gnome-fs-trash-full.svg
/usr/share/icons/gnome/scalable/status/gnome-stock-trash-full.svg
/usr/share/icons/gnome/scalable/status/stock_trash_full.svg
/usr/share/icons/gnome/scalable/status/trashcan_full.svg
/usr/share/icons/gnome/scalable/status/user-trash-full.svg
/usr/share/icons/gnome/scalable/status/xfce-trash_full.svg
/usr/share/icons/hicolor/32x32/mimetypes/karchiveur_trash.png
/usr/share/icons/locolor/16x16/mimetypes/karchiveur_trash.png
/usr/share/icons/locolor/22x22/mimetypes/karchiveur_trash.png
/usr/share/icons/oxygen/128x128/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/128x128/places/user-trash.png
/usr/share/icons/oxygen/128x128/status/user-trash-full.png
/usr/share/icons/oxygen/16x16/actions/trash-empty.png
/usr/share/icons/oxygen/16x16/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/16x16/places/user-trash.png
/usr/share/icons/oxygen/16x16/status/user-trash-full.png
/usr/share/icons/oxygen/22x22/actions/trash-empty.png
/usr/share/icons/oxygen/22x22/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/22x22/places/user-trash.png
/usr/share/icons/oxygen/22x22/status/user-trash-full.png
/usr/share/icons/oxygen/32x32/actions/trash-empty.png
/usr/share/icons/oxygen/32x32/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/32x32/places/user-trash.png
/usr/share/icons/oxygen/32x32/status/user-trash-full.png
/usr/share/icons/oxygen/48x48/actions/trash-empty.png
/usr/share/icons/oxygen/48x48/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/48x48/places/user-trash.png
/usr/share/icons/oxygen/48x48/status/user-trash-full.png
/usr/share/icons/oxygen/64x64/mimetypes/application-x-trash.png
/usr/share/icons/oxygen/64x64/places/user-trash.png
/usr/share/icons/oxygen/64x64/status/user-trash-full.png
/usr/share/kde4/services/plasma-applet-trash.desktop
/usr/share/kde4/services/trash.protocol
/usr/share/mime/application/x-trash.xml
/usr/share/mimelnk/application/x-trash.desktop
/usr/share/omf/trashapplet
/usr/share/omf/trashapplet/trashapplet-C.omf
/usr/share/omf/trashapplet/trashapplet-ca.omf
/usr/share/omf/trashapplet/trashapplet-da.omf
/usr/share/omf/trashapplet/trashapplet-de.omf
/usr/share/omf/trashapplet/trashapplet-el.omf
/usr/share/omf/trashapplet/trashapplet-en_GB.omf
/usr/share/omf/trashapplet/trashapplet-es.omf
/usr/share/omf/trashapplet/trashapplet-fi.omf
/usr/share/omf/trashapplet/trashapplet-fr.omf
/usr/share/omf/trashapplet/trashapplet-hu.omf
/usr/share/omf/trashapplet/trashapplet-it.omf
/usr/share/omf/trashapplet/trashapplet-nl.omf
/usr/share/omf/trashapplet/trashapplet-oc.omf
/usr/share/omf/trashapplet/trashapplet-pa.omf
/usr/share/omf/trashapplet/trashapplet-pt_BR.omf
/usr/share/omf/trashapplet/trashapplet-ru.omf
/usr/share/omf/trashapplet/trashapplet-sv.omf
/usr/share/omf/trashapplet/trashapplet-uk.omf
/usr/share/omf/trashapplet/trashapplet-zh_HK.omf
/usr/share/omf/trashapplet/trashapplet-zh_TW.omf
/usr/share/screenlets/Trash
/usr/share/screenlets/Trash/TrashScreenlet.py
/usr/share/screenlets/Trash/TrashScreenlet.pyc
/usr/share/screenlets/Trash/icon.png
/usr/share/screenlets/Trash/themes
/usr/share/screenlets/Trash/themes/default
/usr/share/screenlets/Trash/themes/default/user-trash-empty.png
/usr/share/screenlets/Trash/themes/default/user-trash-full.png
/usr/share/sounds/KDE-Sys-Trash-Emptied.ogg
sufy@sufy-laptop:~$ 

```

---

### Post by andrew.46 on 2009-03-14
Hi,

Try:

```
ls -l /root/.local/share/Trash
```

Andrew

---

### Post by photon_man62 on 2009-03-14
Just right-click on the trash icon and click "Empty Trash" while in an admin account.

I mean, it said it could not DISPLAY all the ocntents, which means they might still be there.

---

### Post by suffer1989 on 2009-03-15
> **andrew.46 said:**
> Hi,

Try:

```
ls -l /root/.local/share/Trash
```

Andrew

I get 

```
sufy@sufy-laptop:~$ sudo ls -l /root/.local/share/Trash
[sudo] password for sufy: 
total 8
drwx------ 4 root root 4096 2009-03-14 22:19 files
drwx------ 2 root root 4096 2009-03-14 22:19 info
sufy@sufy-laptop:~$ 

```

> photon_man62]

 Just right-click on the trash icon and click "Empty Trash" while in an admin account.

I mean, it said it could not DISPLAY all the ocntents, which means they might still be there. 

Ive tried Sudo nautilus, but i get 

Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by andrew.46 on 2009-03-15
Hi suffer1989,

> **suffer1989 said:**
> 
```
sufy@sufy-laptop:~$ sudo ls -l /root/.local/share/Trash
[sudo] password for sufy: 
total 8
drwx------ 4 root root 4096 2009-03-14 22:19 files
drwx------ 2 root root 4096 2009-03-14 22:19 info
sufy@sufy-laptop:~$ 

```

Oops I forgot the structure of this folder :-). The following should do it:

```
sudo ls -l /root/.local/share/Trash/files
```

Andrew

---

### Post by suffer1989 on 2009-03-20
> **andrew.46 said:**
> Hi suffer1989,



Oops I forgot the structure of this folder :-). The following should do it:

```
sudo ls -l /root/.local/share/Trash/files
```

Andrew



BUMP

Sorry for the late response 



I get :

```
sufy@sufy-laptop:~$ sudo ls -l /root/.local/share/Trash/files
total 8
drwxr-xr-x 8 sufy sufy 4096 2009-03-14 22:17 Doovd
drwxr-xr-x 2 root root 4096 2008-11-11 20:11 vbox
sufy@sufy-laptop:~$ 

```


How can I delete these hidden files ?

---

### Post by XanTrax on 2009-03-20
> **suffer1989 said:**
> BUMP

Sorry for the late response 



I get :

```
sufy@sufy-laptop:~$ sudo ls -l /root/.local/share/Trash/files
total 8
drwxr-xr-x 8 sufy sufy 4096 2009-03-14 22:17 Doovd
drwxr-xr-x 2 root root 4096 2008-11-11 20:11 vbox
sufy@sufy-laptop:~$ 

```


How can I delete these hidden files ?

Try this:

```

sudo su -
<enter password>
cd /root/.local/share/Trash/files
rm -rfv *. && rm -rfv *

```

---

### Post by suffer1989 on 2009-03-21
> **XanTrax said:**
> Try this:

```

sudo su -
<enter password>
cd /root/.local/share/Trash/files
rm -rfv *. && rm -rfv *

```


Thanks that works, perfectly.

---

