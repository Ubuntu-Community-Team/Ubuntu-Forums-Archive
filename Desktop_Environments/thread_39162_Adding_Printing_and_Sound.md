---
title: "Adding Printing and Sound"
date: 2005-06-03
forum: Desktop Environments
---

### Post by sciurus on 2005-06-03
My office has several spare Pentium II's that I'd like to configure with Ubuntu and XFCE. If I first install Ubuntu with the server option and then install these packages, will it give me a working desktop system with less memory usage than a standard install? What I'm unsure about making work is printing and sound support.

x_packages="x-window-system-core xfce4 gdm gnome-sudo" 

power_packages="acpi acpid powermanagement-interface"

fonts_packages="msttcorefonts ttf-bitstream-vera ttf-freefont x-ttcidfont-conf"

print_packages="cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint foomatic-db foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters-foomatic filters-ppds gnome_cups_manager"

office_packages="xpdf openoffice.org openoffice.org-l10n-en openoffice.org-help-en openoffice.org-hyphenation-en-us myspell-en-us openoffice.org-thesaurus-en-us openoffice.org-gtk-gnome"

graphics_packages="eog gthumb xsane gimp gimp-python"

internet_packages="mozilla-firefox gaim gftp tsclient"

media_packages="esound mplayer-586 mplayer-fonts"

plugin_packages="mozilla-mplayer sun-j2re1.5 flashplayer-mozilla"

misc_packages="gnome-volume-manager synaptic file-roller smbclient smbfs wine"

Also, I would appreciate any alternate application recommendations; right now it's still very GNOMEish.

---

### Post by Joeb on 2005-06-03
Since it appears that you are trying to create desktops instead of servers, why not just do the default install with gnome and then add XFCE?  You can then set XFCE as the default WM.  Assuming you are not extremely tight on disk space, the advantage of this approach would be that if something isn't working as expected in XFCE, you could go into gnome and troubleshoot it (although slowly on a RAM/CPU limited machine).  Or, if space is tight, you could do the default install then remove gnome and add XFCE.  All of your other gui apps you list should survive (although you will have to add them to the taskbar or menu in XFCE).

---

### Post by sciurus on 2005-06-04
I suppose that's what I'll end up doing, just for the ease of it. What I was hoping is that people would have sugestions for replacements for the Gnome apps that might be a little lighter, require fewer libraries, etc.

---

### Post by Joeb on 2005-06-04
Most of the packages you listed in your post aren't actually gnome applications, nor do they even use the gnome libraries (although some do use the gtk libraries).  As an example, firefox should use the same resources whether under gnome, kde or XFCE.  Same with most of your listed apps.

There are some definate alternatives to the apps listed, though.  For instance, while Openoffice.org is great, if you don't need a spreadsheet, presentation program, etc.  Abiword might better fit the bill.  It's still MS-Word compatable, but doesn't have nearly as large of a footprint as Openoffice.org.  There's also gnumeric for a spreadsheet.

The Microsoft fonts you list, don't really take up anything other than diskspace.  However, if that is tight, you don't really need to install them as there are plenty installed with Ubuntu.

You do probably want to leave all of the printing stuff you mentioned.  Cups definately is worth the tradeoff on printing.  However, even though Cups uses the gimp drivers, that doesn't mean you have to install the gimp application, unless you are planning on doing graphics work.  Same with xsane, unless you have a scanner.

With the exception of mplayer, most of the rest of the stuff you list are not really that resource intensive.  You might try googling for mplayer alternatives, though, because there are quite a few.

But, back to gnome apps themselves.  Gnome doesn't have a bunch of gnome specific apps like KDE does, however, it does have core functionality that run as individual apps, like the taskbar and volume manager, etc.  However, if you are running XFCE, these won't affect your performance as they aren't loaded into memory unless gnome is running.  Most of them, however, aren't very resource intensive and do provide functionality that you would want, even with XFCE (the gnome-volume-manager comes to mind).  

That said, the most resource intensive gnome application is nautilus.  Using XFCE's filemanger, although not as pretty, will definately safe on resources.  XFCE, itself, is pretty lean on resource use.  So, even with the apps listed, since the WM will be using less resources, more will be available for the apps and you should see a noticable improvement.

The nice thing about having the underlying gnome libraries installed (and kde, for that matter) is that should you need a gnome app, it will run.  If you don't really have the room for the full blown gnome to be installed, you could always uninstall it after installing XFCE and before installing your other apps of choice.  That way, if one of them depends on some gnome libraries, synaptic will handle the dependencies and you will only install the minimu libraries you need.


Joeb

ps.  evidently, there are quite a few XFCE Ubuntu users out there.  They might not see your post under the description of printing and sound.  You might want to post again with a description like "What apps are good for a low resource XFCE install?"  That seems to be what you are really asking.

---

### Post by sciurus on 2005-06-05
My main concern was how to get printing and sound working for people who do [this sort](http://ubuntuforums.org/showthread.php?t=30896&highlight=xfce4) of installation.

Glad to hear most of the apps are relatively light. I just feel silly using things like Eye of Gnome or gnome_cups_manager if there are good alternatives. I'll see how Gnumeric works with the spreadsheets we use; maybe it and Abiword can replace OpenOffice if their MS Office compatibity is good. I picked mplayer because of its wide format support and, more importantly, mozilla plugin; I'll look around though.

---

### Post by andlinux21 on 2005-07-01
I would like to know how to get sound in xfce4 or fluxbox I have sound in gnome it took me awhile to get it working but when i switch WM to anything other than gnome it doesnt work....

---

