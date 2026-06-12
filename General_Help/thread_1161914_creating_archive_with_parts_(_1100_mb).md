---
title: "creating archive with parts ( 1*100 mb)"
date: 2009-05-17
forum: General Help
---

### Post by themacedonian on 2009-05-17
how i can create partitions with .rar in ubuntu like in windows with win rar

view picture >>

[IMG]http://forums.mystery-axiom.com/images/FAQ/handle_rar/winrar-rar-3-sizei7Vh.jpg[/IMG]

thanks in advance):P

---

### Post by Joeb454 on 2009-05-17
```
sudo apt-get install rar
```

Then select what you want to archive in the file browser - right click, and choose create archive.

This brings up a list, which you then choose the file extension for (in this case - rar) and you can split it into archives :)

---

### Post by themacedonian on 2009-05-23
Ok. When i click create archive, i dont have another menu, creating archive start directly and when archive will created i have just one part ( all files here) 
How i can share partitions ? 
for example file, i wanna share with another ppl and upload on rapidshare.
file is 500 mb and i like upload partitions with 100 mb. How i can make this ?

---

### Post by mcduck on 2009-05-23
> **themacedonian said:**
> Ok. When i click create archive, i dont have another menu, creating archive start directly and when archive will created i have just one part ( all files here) 
How i can share partitions ? 
for example file, i wanna share with another ppl and upload on rapidshare.
file is 500 mb and i like upload partitions with 100 mb. How i can make this ?

Seriously? You don't get a window asking what name you want to give to the archive, waht type of archive to create and where?

What version of Ubuntu you are using (and what desktop environment)?

---

### Post by themacedonian on 2009-05-23
Folder : Right click to him. Create archive. No menu for making partitions, just start directly creating ONE :S In this ONE partition, here is all files.

I am using ubuntu 8.10 and desctop is gnome. Please give me any solution for making partitions :(

---

### Post by mcduck on 2009-05-23
You really don't get a window like this after selecting "Create Archive" from the right-click menu?

---

### Post by michy99 on 2009-05-23
I do it from the command line.```
rar a -v100m -pmoney test filename
```
This will put the file named 'filename' into an archive split into 100 MB volumes named test.part1.rar, test.part2,rar, etc. The -pmoney switch encrypts with the password 'money'. If you don't want password leave it off. To learn all the options for rar enter```
man rar
```

---

### Post by themacedonian on 2009-05-23
Exactly, this is my problem. View picture please :(

[IMG]http://i39.tinypic.com/2iub15d.png[/IMG]

Sugestion ?

---

### Post by themacedonian on 2009-05-23
Exactly, this is my problem. View picture please :(

[IMG]http://i39.tinypic.com/2iub15d.png[/IMG]

Sugestion ?

---

### Post by mcduck on 2009-05-23
Have you tried first setting the archive type to rar? Perhaps the "Other Options"-button will then appear (most of the archive types don't have any options to configure)..

If not, you'll pretty much have to either create the archive from command line, or try using the full Archive Manager-program instead of the quick option from the Nautilus right-click menu.

There is no option for disabling that "Other Options"-button anywhere, not in Archive Managers settings and not even in gconf-editor. Actually if that button was missing on my system I'd start by reinstalling the archive manager because something is definitely broken..

---

### Post by Legace on 2009-05-23
Make sure to select RAR:
[img]http://ubuntuforums.org/attachment.php?attachmentid=114808&stc=1&d=1243097131[/img]

---

### Post by themacedonian on 2009-05-23
yes, i am sure that arcive menager is on RAR 100%

If my archive menager is broken, please tell me steps for uninstalling and istalling again.

thank you in advance

---

### Post by themacedonian on 2009-05-23
no help for me ? :o:o

---

### Post by Legace on 2009-05-23
Open Synaptic.
Search for **file-roller**
Right-click on the file-roller entry, and select "Mark for reinstallation".

Then press Apply and wait.

---

### Post by themacedonian on 2009-05-23
uninstall and install and its again the same. No button for more options and make partitions :S:S
what is the problem i dont know :S

PLEASE tell me all steps to have menu like your menu.

 thanks in advance

---

### Post by themacedonian on 2009-05-23
and ? :(

---

### Post by michy99 on 2009-05-23
I think that probably Legace is using a newer version of archive manager. I also cannot split into volumes by right-clicking, which is why I use the command line. (You did see my reply above didn't you?) Legace is probably running 9.04 and it probably has a newer version of file-roller in the repositories. I suppose you could download and install the latest version from the website.

[http://fileroller.sourceforge.net/](http://fileroller.sourceforge.net/)

---

### Post by mcduck on 2009-05-23
> **michy99 said:**
> I think that probably Legace is using a newer version of archive manager. I also cannot split into volumes by right-clicking, which is why I use the command line. (You did see my reply above didn't you?) Legace is probably running 9.04 and it probably has a newer version of file-roller in the repositories. I suppose you could download and install the latest version from the website.

[http://fileroller.sourceforge.net/](http://fileroller.sourceforge.net/)

That could be it, although the feature has been there for quite a long time now..

---

### Post by themacedonian on 2009-05-24
ok. i have download newest verzion of file roller from here
[http://ftp.gnome.org/pub/gnome/sources/file-roller/2.24/file-roller-2.24.3.tar.gz](http://ftp.gnome.org/pub/gnome/sources/file-roller/2.24/file-roller-2.24.3.tar.gz)
now its on my desktop. please tell me how to install this. I want install with using gnome terminal.

---

### Post by themacedonian on 2009-05-24
i tried make partitions with archive menager with rolling files, but problem its here

[IMG]http://i43.tinypic.com/2wofz9w.png[/IMG]

help ?

---

### Post by Legace on 2009-05-24
> **themacedonian said:**
> ok. i have download newest verzion of file roller from here
[http://ftp.gnome.org/pub/gnome/sources/file-roller/2.24/file-roller-2.24.3.tar.gz](http://ftp.gnome.org/pub/gnome/sources/file-roller/2.24/file-roller-2.24.3.tar.gz)
now its on my desktop. please tell me how to install this. I want install with using gnome terminal.

Download the file-roller tar.gz package to your desktop. Extract it to your desktop.
Then open Terminal and type in the following:
```
cd '~/Desktop/file-roller-2.24.3'
```

Then type in:
```
sudo ./install-sh
```

---

### Post by themacedonian on 2009-05-24
> **Legace said:**
> Download the file-roller tar.gz package to your desktop. Extract it to your desktop.
Then open Terminal and type in the following:
```
cd '~/Desktop/file-roller-2.24.3'
```

Then type in:
```
sudo ./install-sh
```

bash: cd: ~/Desktop/file-roller-2.24.3 No such file or directory


:S:S:S

---

### Post by themacedonian on 2009-05-24
> root@****-desktop:/home/****/Desktop# tar xvf file-roller-2.24.3.tar.gz
file-roller-2.24.3/
file-roller-2.24.3/COPYING
file-roller-2.24.3/src/
file-roller-2.24.3/src/fr-command-iso.c
file-roller-2.24.3/src/gconf-utils.c
file-roller-2.24.3/src/eggtreemultidnd.h
file-roller-2.24.3/src/file-utils.h
file-roller-2.24.3/src/fr-process.h
file-roller-2.24.3/src/fr-command-zip.h
file-roller-2.24.3/src/fr-command-rpm.h
file-roller-2.24.3/src/preferences.h
file-roller-2.24.3/src/dlg-prop.h
file-roller-2.24.3/src/fr-marshal.h
file-roller-2.24.3/src/fr-command-rar.c
file-roller-2.24.3/src/sexy-icon-entry.c
file-roller-2.24.3/src/mkdtemp.c
file-roller-2.24.3/src/glib-utils.c
file-roller-2.24.3/src/dlg-add-folder.c
file-roller-2.24.3/src/main.c
file-roller-2.24.3/src/dlg-new.h
file-roller-2.24.3/src/fr-command.h
file-roller-2.24.3/src/dlg-delete.c
file-roller-2.24.3/src/fr-marshal.list
file-roller-2.24.3/src/dlg-add-files.c
file-roller-2.24.3/src/fr-process.c
file-roller-2.24.3/src/fr-command-iso.h
file-roller-2.24.3/src/sh/
file-roller-2.24.3/src/sh/Makefile.in
file-roller-2.24.3/src/sh/Makefile.am
file-roller-2.24.3/src/sh/isoinfo.sh
file-roller-2.24.3/src/dlg-password.c
file-roller-2.24.3/src/fr-command-zoo.c
file-roller-2.24.3/src/dlg-update.c
file-roller-2.24.3/src/sexy-icon-entry.h
file-roller-2.24.3/src/open-file.c
file-roller-2.24.3/src/fr-archive.h
file-roller-2.24.3/src/fr-command-jar.h
file-roller-2.24.3/src/dlg-add-files.h
file-roller-2.24.3/src/eggtreemultidnd.c
file-roller-2.24.3/src/fr-command-tar.h
file-roller-2.24.3/src/fr-command-rpm.c
file-roller-2.24.3/src/dlg-ask-password.c
file-roller-2.24.3/src/Makefile.in
file-roller-2.24.3/src/fr-command-7z.h
file-roller-2.24.3/src/ui.h
file-roller-2.24.3/src/fr-marshal.c
file-roller-2.24.3/src/dlg-open-with.c
file-roller-2.24.3/src/fr-command-ace.h
file-roller-2.24.3/src/fr-command-arj.c
file-roller-2.24.3/src/dlg-extract.h
file-roller-2.24.3/src/fr-command-lha.c
file-roller-2.24.3/src/gio-utils.h
file-roller-2.24.3/src/gtk-utils.h
file-roller-2.24.3/src/dlg-new.c
file-roller-2.24.3/src/dlg-batch-add.c
file-roller-2.24.3/src/dlg-ask-password.h
file-roller-2.24.3/src/fr-command-ar.h
file-roller-2.24.3/src/file-utils.c
file-roller-2.24.3/src/java-utils.c
file-roller-2.24.3/src/actions.c
file-roller-2.24.3/src/fr-command-zoo.h
file-roller-2.24.3/src/fr-list-model.h
file-roller-2.24.3/src/fr-stock.h
file-roller-2.24.3/src/fr-command-alz.h
file-roller-2.24.3/src/fr-command-cpio.h
file-roller-2.24.3/src/fr-archive.c
file-roller-2.24.3/src/fr-command-7z.c
file-roller-2.24.3/src/fr-command-tar.c
file-roller-2.24.3/src/fr-command-zip.c
file-roller-2.24.3/src/fr-command-jar.c
file-roller-2.24.3/src/dlg-password.h
file-roller-2.24.3/src/fr-command-ar.c
file-roller-2.24.3/src/glib-utils.h
file-roller-2.24.3/src/fr-command-unstuff.h
file-roller-2.24.3/src/fr-stock.c
file-roller-2.24.3/src/main.h
file-roller-2.24.3/src/dlg-extract.c
file-roller-2.24.3/src/open-file.h
file-roller-2.24.3/src/fr-window.c
file-roller-2.24.3/src/file-data.h
file-roller-2.24.3/src/typedefs.h
file-roller-2.24.3/src/java-utils.h
file-roller-2.24.3/src/fr-command-cfile.c
file-roller-2.24.3/src/fr-command-ace.c
file-roller-2.24.3/src/fr-command-cfile.h
file-roller-2.24.3/src/dlg-add-folder.h
file-roller-2.24.3/src/Makefile.am
file-roller-2.24.3/src/dlg-batch-add.h
file-roller-2.24.3/src/mkdtemp.h
file-roller-2.24.3/src/fr-command-cpio.c
file-roller-2.24.3/src/fr-command-arj.h
file-roller-2.24.3/src/dlg-prop.c
file-roller-2.24.3/src/dlg-update.h
file-roller-2.24.3/src/fr-command-rar.h
file-roller-2.24.3/src/gio-utils.c
file-roller-2.24.3/src/fr-command-unstuff.c
file-roller-2.24.3/src/fr-error.c
file-roller-2.24.3/src/dlg-open-with.h
file-roller-2.24.3/src/file-data.c
file-roller-2.24.3/src/actions.h
file-roller-2.24.3/src/fr-command.c
file-roller-2.24.3/src/gconf-utils.h
file-roller-2.24.3/src/gtk-utils.c
file-roller-2.24.3/src/fr-window.h
file-roller-2.24.3/src/fr-error.h
file-roller-2.24.3/src/fr-command-lha.h
file-roller-2.24.3/src/fr-command-alz.c
file-roller-2.24.3/src/preferences.c
file-roller-2.24.3/src/dlg-delete.h
file-roller-2.24.3/src/fr-enum-types.h
file-roller-2.24.3/src/fr-list-model.c
file-roller-2.24.3/src/fr-enum-types.c
file-roller-2.24.3/missing
file-roller-2.24.3/NEWS
file-roller-2.24.3/help/
file-roller-2.24.3/help/ca/
file-roller-2.24.3/help/ca/file-roller.xml
file-roller-2.24.3/help/ca/figures/
file-roller-2.24.3/help/ca/figures/file-roller_home.png
file-roller-2.24.3/help/ca/figures/file-roller_uparrow.png
file-roller-2.24.3/help/ca/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/ca/figures/file-roller_main_window.png
file-roller-2.24.3/help/ca/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/ca/ca.po
file-roller-2.24.3/help/oc/
file-roller-2.24.3/help/oc/file-roller.xml
file-roller-2.24.3/help/oc/oc.po
file-roller-2.24.3/help/fi/
file-roller-2.24.3/help/fi/file-roller.xml
file-roller-2.24.3/help/fi/fi.po
file-roller-2.24.3/help/fi/figures/
file-roller-2.24.3/help/fi/figures/file-roller_home.png
file-roller-2.24.3/help/fi/figures/file-roller_uparrow.png
file-roller-2.24.3/help/fi/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/fi/figures/file-roller_main_window.png
file-roller-2.24.3/help/fi/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/C/
file-roller-2.24.3/help/C/file-roller.xml
file-roller-2.24.3/help/C/figures/
file-roller-2.24.3/help/C/figures/file-roller_home.png
file-roller-2.24.3/help/C/figures/file-roller_uparrow.png
file-roller-2.24.3/help/C/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/C/figures/file-roller_main_window.png
file-roller-2.24.3/help/C/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/C/legal.xml
file-roller-2.24.3/help/vi/
file-roller-2.24.3/help/vi/file-roller.xml
file-roller-2.24.3/help/vi/vi.po
file-roller-2.24.3/help/it/
file-roller-2.24.3/help/it/file-roller.xml
file-roller-2.24.3/help/it/figures/
file-roller-2.24.3/help/it/figures/file-roller_home.png
file-roller-2.24.3/help/it/figures/file-roller_uparrow.png
file-roller-2.24.3/help/it/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/it/figures/file-roller_main_window.png
file-roller-2.24.3/help/it/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/it/it.po
file-roller-2.24.3/help/fr/
file-roller-2.24.3/help/fr/file-roller.xml
file-roller-2.24.3/help/fr/fr.po
file-roller-2.24.3/help/fr/figures/
file-roller-2.24.3/help/fr/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/fr/figures/file-roller_main_window.png
file-roller-2.24.3/help/Makefile.in
file-roller-2.24.3/help/uk/
file-roller-2.24.3/help/uk/file-roller.xml
file-roller-2.24.3/help/uk/figures/
file-roller-2.24.3/help/uk/figures/file-roller_home.png
file-roller-2.24.3/help/uk/figures/file-roller_uparrow.png
file-roller-2.24.3/help/uk/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/uk/figures/file-roller_main_window.png
file-roller-2.24.3/help/uk/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/uk/uk.po
file-roller-2.24.3/help/sv/
file-roller-2.24.3/help/sv/file-roller.xml
file-roller-2.24.3/help/sv/sv.po
file-roller-2.24.3/help/sv/figures/
file-roller-2.24.3/help/sv/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/sv/figures/file-roller_main_window.png
file-roller-2.24.3/help/file-roller.omf.in
file-roller-2.24.3/help/nl/
file-roller-2.24.3/help/nl/file-roller.xml
file-roller-2.24.3/help/nl/nl.po
file-roller-2.24.3/help/es/
file-roller-2.24.3/help/es/es.po
file-roller-2.24.3/help/es/file-roller.xml
file-roller-2.24.3/help/es/figures/
file-roller-2.24.3/help/es/figures/file-roller_home.png
file-roller-2.24.3/help/es/figures/file-roller_uparrow.png
file-roller-2.24.3/help/es/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/es/figures/file-roller_main_window.png
file-roller-2.24.3/help/es/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/bg/
file-roller-2.24.3/help/bg/file-roller.xml
file-roller-2.24.3/help/bg/figures/
file-roller-2.24.3/help/bg/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/bg/figures/file-roller_main_window.png
file-roller-2.24.3/help/bg/bg.po
file-roller-2.24.3/help/Makefile.am
file-roller-2.24.3/help/de/
file-roller-2.24.3/help/de/file-roller.xml
file-roller-2.24.3/help/de/figures/
file-roller-2.24.3/help/de/figures/file-roller_home.png
file-roller-2.24.3/help/de/figures/file-roller_uparrow.png
file-roller-2.24.3/help/de/figures/file-roller_leftarrow.png
file-roller-2.24.3/help/de/figures/file-roller_main_window.png
file-roller-2.24.3/help/de/figures/file-roller_rightarrow.png
file-roller-2.24.3/help/de/de.po
file-roller-2.24.3/help/ChangeLog
file-roller-2.24.3/help/ru/
file-roller-2.24.3/help/ru/file-roller.xml
file-roller-2.24.3/help/ru/ru.po
file-roller-2.24.3/MAINTAINERS
file-roller-2.24.3/nautilus/
file-roller-2.24.3/nautilus/Makefile.in
file-roller-2.24.3/nautilus/nautilus-fileroller.h
file-roller-2.24.3/nautilus/Makefile.am
file-roller-2.24.3/nautilus/nautilus-fileroller.c
file-roller-2.24.3/nautilus/fileroller-module.c
file-roller-2.24.3/configure
file-roller-2.24.3/gnome-doc-utils.make
file-roller-2.24.3/Makefile.in
file-roller-2.24.3/TODO
file-roller-2.24.3/AUTHORS
file-roller-2.24.3/depcomp
file-roller-2.24.3/config.h.in
file-roller-2.24.3/data/
file-roller-2.24.3/data/file-roller.desktop.in
file-roller-2.24.3/data/glade/
file-roller-2.24.3/data/glade/new.glade
file-roller-2.24.3/data/glade/batch-password.glade
file-roller-2.24.3/data/glade/properties.glade
file-roller-2.24.3/data/glade/add-options.glade
file-roller-2.24.3/data/glade/open-with.glade
file-roller-2.24.3/data/glade/batch-add-files.glade
file-roller-2.24.3/data/glade/Makefile.in
file-roller-2.24.3/data/glade/password.glade
file-roller-2.24.3/data/glade/update.glade
file-roller-2.24.3/data/glade/Makefile.am
file-roller-2.24.3/data/glade/delete.glade
file-roller-2.24.3/data/icons/
file-roller-2.24.3/data/icons/scalable/
file-roller-2.24.3/data/icons/scalable/apps/
file-roller-2.24.3/data/icons/scalable/apps/Makefile.in
file-roller-2.24.3/data/icons/scalable/apps/Makefile.am
file-roller-2.24.3/data/icons/scalable/apps/file-roller.svg
file-roller-2.24.3/data/icons/scalable/Makefile.in
file-roller-2.24.3/data/icons/scalable/Makefile.am
file-roller-2.24.3/data/icons/Makefile.in
file-roller-2.24.3/data/icons/16x16/
file-roller-2.24.3/data/icons/16x16/apps/
file-roller-2.24.3/data/icons/16x16/apps/file-roller.png
file-roller-2.24.3/data/icons/16x16/apps/Makefile.in
file-roller-2.24.3/data/icons/16x16/apps/Makefile.am
file-roller-2.24.3/data/icons/16x16/Makefile.in
file-roller-2.24.3/data/icons/16x16/actions/
file-roller-2.24.3/data/icons/16x16/actions/add-files-to-archive.png
file-roller-2.24.3/data/icons/16x16/actions/extract-archive.png
file-roller-2.24.3/data/icons/16x16/actions/Makefile.in
file-roller-2.24.3/data/icons/16x16/actions/add-folder-to-archive.png
file-roller-2.24.3/data/icons/16x16/actions/Makefile.am
file-roller-2.24.3/data/icons/16x16/Makefile.am
file-roller-2.24.3/data/icons/22x22/
file-roller-2.24.3/data/icons/22x22/apps/
file-roller-2.24.3/data/icons/22x22/apps/file-roller.png
file-roller-2.24.3/data/icons/22x22/apps/Makefile.in
file-roller-2.24.3/data/icons/22x22/apps/Makefile.am
file-roller-2.24.3/data/icons/22x22/Makefile.in
file-roller-2.24.3/data/icons/22x22/Makefile.am
file-roller-2.24.3/data/icons/32x32/
file-roller-2.24.3/data/icons/32x32/apps/
file-roller-2.24.3/data/icons/32x32/apps/file-roller.png
file-roller-2.24.3/data/icons/32x32/apps/Makefile.in
file-roller-2.24.3/data/icons/32x32/apps/Makefile.am
file-roller-2.24.3/data/icons/32x32/Makefile.in
file-roller-2.24.3/data/icons/32x32/Makefile.am
file-roller-2.24.3/data/icons/Makefile.am
file-roller-2.24.3/data/icons/24x24/
file-roller-2.24.3/data/icons/24x24/apps/
file-roller-2.24.3/data/icons/24x24/apps/file-roller.png
file-roller-2.24.3/data/icons/24x24/apps/Makefile.in
file-roller-2.24.3/data/icons/24x24/apps/Makefile.am
file-roller-2.24.3/data/icons/24x24/Makefile.in
file-roller-2.24.3/data/icons/24x24/actions/
file-roller-2.24.3/data/icons/24x24/actions/add-files-to-archive.png
file-roller-2.24.3/data/icons/24x24/actions/extract-archive.png
file-roller-2.24.3/data/icons/24x24/actions/Makefile.in
file-roller-2.24.3/data/icons/24x24/actions/add-folder-to-archive.png
file-roller-2.24.3/data/icons/24x24/actions/Makefile.am
file-roller-2.24.3/data/icons/24x24/Makefile.am
file-roller-2.24.3/data/Makefile.in
file-roller-2.24.3/data/file-roller.desktop
file-roller-2.24.3/data/file-roller.desktop.in.in
file-roller-2.24.3/data/Makefile.am
file-roller-2.24.3/data/file-roller.schemas
file-roller-2.24.3/config.sub
file-roller-2.24.3/intltool-update.in
file-roller-2.24.3/README
file-roller-2.24.3/HACKING
file-roller-2.24.3/file-roller.spec.in
file-roller-2.24.3/intltool-extract.in
file-roller-2.24.3/config.guess
file-roller-2.24.3/INSTALL
file-roller-2.24.3/Makefile.am
file-roller-2.24.3/mkinstalldirs
file-roller-2.24.3/file-roller.spec
file-roller-2.24.3/aclocal.m4
file-roller-2.24.3/ChangeLog
file-roller-2.24.3/configure.ac
file-roller-2.24.3/intltool-merge.in
file-roller-2.24.3/po/
file-roller-2.24.3/po/te.po
file-roller-2.24.3/po/he.po
file-roller-2.24.3/po/is.po
file-roller-2.24.3/po/lt.po
file-roller-2.24.3/po/nn.po
file-roller-2.24.3/po/fa.po
file-roller-2.24.3/po/gu.po
file-roller-2.24.3/po/ga.po
file-roller-2.24.3/po/be@latin.po
file-roller-2.24.3/po/es.po
file-roller-2.24.3/po/Makefile.in.in
file-roller-2.24.3/po/nb.po
file-roller-2.24.3/po/ms.po
file-roller-2.24.3/po/zh_HK.po
file-roller-2.24.3/po/cy.po
file-roller-2.24.3/po/ko.po
file-roller-2.24.3/po/sq.po
file-roller-2.24.3/po/kn.po
file-roller-2.24.3/po/sk.po
file-roller-2.24.3/po/mg.po
file-roller-2.24.3/po/sl.po
file-roller-2.24.3/po/zh_CN.po
file-roller-2.24.3/po/pt_BR.po
file-roller-2.24.3/po/da.po
file-roller-2.24.3/po/pt.po
file-roller-2.24.3/po/ne.po
file-roller-2.24.3/po/en_CA.po
file-roller-2.24.3/po/sr.po
file-roller-2.24.3/po/ro.po
file-roller-2.24.3/po/hi.po
file-roller-2.24.3/po/fi.po
file-roller-2.24.3/po/ar.po
file-roller-2.24.3/po/et.po
file-roller-2.24.3/po/bs.po
file-roller-2.24.3/po/xh.po
file-roller-2.24.3/po/eu.po
file-roller-2.24.3/po/am.po
file-roller-2.24.3/po/ru.po
file-roller-2.24.3/po/fr.po
file-roller-2.24.3/po/sv.po
file-roller-2.24.3/po/fur.po
file-roller-2.24.3/po/POTFILES.skip
file-roller-2.24.3/po/si.po
file-roller-2.24.3/po/id.po
file-roller-2.24.3/po/ca.po
file-roller-2.24.3/po/zh_TW.po
file-roller-2.24.3/po/pl.po
file-roller-2.24.3/po/ml.po
file-roller-2.24.3/po/sr@latin.po
file-roller-2.24.3/po/ur_PK.po
file-roller-2.24.3/po/oc.po
file-roller-2.24.3/po/th.po
file-roller-2.24.3/po/lv.po
file-roller-2.24.3/po/or.po
file-roller-2.24.3/po/bn_IN.po
file-roller-2.24.3/po/ur.po
file-roller-2.24.3/po/rw.po
file-roller-2.24.3/po/tr.po
file-roller-2.24.3/po/sr@ije.po
file-roller-2.24.3/po/bn.po
file-roller-2.24.3/po/ta.po
file-roller-2.24.3/po/cs.po
file-roller-2.24.3/po/POTFILES.in
file-roller-2.24.3/po/mk.po
file-roller-2.24.3/po/dz.po
file-roller-2.24.3/po/hr.po
file-roller-2.24.3/po/uk.po
file-roller-2.24.3/po/en_GB.po
file-roller-2.24.3/po/mr.po
file-roller-2.24.3/po/de.po
file-roller-2.24.3/po/br.po
file-roller-2.24.3/po/af.po
file-roller-2.24.3/po/gl.po
file-roller-2.24.3/po/ps.po
file-roller-2.24.3/po/LINGUAS
file-roller-2.24.3/po/hy.po
file-roller-2.24.3/po/ka.po
file-roller-2.24.3/po/el.po
file-roller-2.24.3/po/ChangeLog
file-roller-2.24.3/po/ku.po
file-roller-2.24.3/po/bg.po
file-roller-2.24.3/po/az.po
file-roller-2.24.3/po/pa.po
file-roller-2.24.3/po/vi.po
file-roller-2.24.3/po/as.po
file-roller-2.24.3/po/it.po
file-roller-2.24.3/po/mn.po
file-roller-2.24.3/po/ja.po
file-roller-2.24.3/po/be.po
file-roller-2.24.3/po/tk.po
file-roller-2.24.3/po/hu.po
file-roller-2.24.3/po/nl.po
file-roller-2.24.3/install-sh
file-roller-2.24.3/ltmain.sh
root@****-desktop:/home/****/Desktop# 

i have extract file -roller, how i can install now ?

---

