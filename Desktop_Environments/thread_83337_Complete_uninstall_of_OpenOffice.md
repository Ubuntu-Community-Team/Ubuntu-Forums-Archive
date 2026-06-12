---
title: "Complete uninstall of OpenOffice"
date: 2005-10-28
forum: Desktop Environments
---

### Post by kevin1 on 2005-10-28
I found V 1.9.129 impossible to use due to frequent key freezes and crashes, so I installed V 1.1.5 via Synaptic. Wishing to try the latest non-beta version, I used Synaptic to uninstall both, marking them for complete removal.

I then used 'locate' to check that nothing remained, and was surprised that the following had not been removed:

/etc/openoffice
/etc/openoffice/dictionary.lst
/var/lib/dpkg/info/openoffice.org2-evolution.list
/var/lib/dpkg/info/openoffice.org2-evolution.postrm
/var/cache/apt/archives/openclipart-openoffice.org_0.13.2+dfsg-1_all.deb
/var/cache/apt/archives/openoffice.org-thesaurus-en-us_1.1.5-0ubuntu1_all.deb
/var/cache/apt/archives/openoffice.org2-help-en-gb_1.9.129-0.1ubuntu5_all.deb
/var/cache/apt/archives/openoffice.org1-debian-files_1.1.5-0+1ubuntu1_all.deb
/var/cache/apt/archives/openoffice.org2-l10n-en-gb_1.9.129-0.1ubuntu3_all.deb
/var/cache/apt/archives/openoffice.org-gnomevfs_1.1.5-0ubuntu1_i386.deb
/var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
/var/cache/apt/archives/openoffice.org-help-en_1.1+20040420-3_all.deb
/var/cache/apt/archives/openoffice.org-gtk-gnome_1.1.5-0ubuntu1_i386.deb
/var/cache/apt/archives/openoffice.org-l10n-en_1.1.5-0ubuntu1_all.deb
/var/cache/apt/archives/openoffice.org-bin_1.1.5-0ubuntu1_i386.deb
/var/cache/apt/archives/openoffice.org_1.1.5-0ubuntu1_all.deb
/usr/sbin/update-openoffice-dicts
/usr/share/man/man8/update-openoffice-dicts.8.gz
/usr/share/fonts/truetype/openoffice
/usr/share/fonts/truetype/openoffice/opens___.ttf
/usr/share/fonts/truetype/openoffice/fonts.cache-1
/usr/share/icons/hicolor/16x16/stock/generic/stock_openoffice.png
/usr/share/icons/hicolor/32x32/stock/generic/stock_openoffice.png
/usr/share/openclipart/png/computer/icons/flat-theme/applications/openoffice.png

Can I safely delete these folders and files before installing the new version?

Thanks,

Kevin

---

### Post by Dr. Nick on 2005-10-28
Most of them shouldnt be a problem, The only ones I am sure shuould be safe to delete would be the ones in /var/cache/apt/archives. I bet you installed Oo over a network and that is just the files it downloaded to install from. Some of the others like the jpg and png are pictues so they shouldnt be a big deal either.

Overall I dont see anything in their that would mess up your system if deleted, but they probably wouldnt mess up the new install of Oo if you just left them and intalled.

---

### Post by kevin1 on 2005-10-28
Thanks for the reply Dr. Nick,

I think I will delete them to be absolutely sure that nothing will mess-up the new installation.

Kevin

---

