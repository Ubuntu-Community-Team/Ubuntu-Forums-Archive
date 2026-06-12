---
title: "Scribus 1.3.x font size problem (0.5pt)"
date: 2006-12-21
forum: Desktop Environments
---

### Post by hrabeX on 2006-12-21
I have problem with Scribus running on Kubuntu. If I try to change default font size in Properties-text tab (12pt), it jumps to 0.5pt value and there is no posibility to change.

When I previously used Scribus on Ubuntu, everything worked fine.

---

### Post by floogy on 2008-06-12
I got the same issue, but as a workaround I can start it with LANG=C scribus, and the error goes away:
 [https://bugs.launchpad.net/uck/+bug/228227](https://bugs.launchpad.net/uck/+bug/228227)

I got these error messages on my console nevertheless I use the workaround or not:
```
qstring_to_xtp result code -2
Qt: Locales not supported on X server
QInputContext: no input method context available
```

It might be a problem of installed fonts:
[https://launchpad.net/ubuntu/+source/scribus/+bug/45565](https://launchpad.net/ubuntu/+source/scribus/+bug/45565)
[http://bugs.scribus.net/view.php?id=4423](http://bugs.scribus.net/view.php?id=4423)
[http://wiki.scribus.net/index.php/Getting_Scribus_on_Ubuntu/Kubuntu_up_and_running#Default_GUI_font_.28Ubuntu_users_only.29](http://wiki.scribus.net/index.php/Getting_Scribus_on_Ubuntu/Kubuntu_up_and_running#Default_GUI_font_.28Ubuntu_users_only.29)

```
$ sudo apt-get remove ttf-indic-fonts-core ttf-indic-fonts 
[...]
The following packages will be REMOVED:
  ttf-indic-fonts ttf-indic-fonts-core
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 1397kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 539062 files and directories currently installed.)
Removing ttf-indic-fonts ...
Removing ttf-indic-fonts-core ...
No CIDSupplement specified for Mikachan-PB-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-P, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for GBZenKai-Medium, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Light, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for UKaiCN, defaulting to 0.
No CIDSupplement specified for Mikachan, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for BousungEG-Light-GB, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-P-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-PS-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-JaH, defaulting to 0.
No CIDSupplement specified for ZenKai-Medium, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Mikachan-PB, defaulting to 0.
No CIDSupplement specified for Mikachan-PS, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core
```

This didn't help at all.

---

### Post by floogy on 2008-06-12
This bug is tagged unfixeable:
[http://bugs.scribus.net/view.php?id=3826](http://bugs.scribus.net/view.php?id=3826)
[https://launchpad.net/ubuntu/+source/qt-x11-free/+bug/68142](https://launchpad.net/ubuntu/+source/qt-x11-free/+bug/68142)
```
sudo apt-get remove scim-qtimm
```
[https://launchpad.net/ubuntu/+source/scribus/+bug/37711](https://launchpad.net/ubuntu/+source/scribus/+bug/37711)
> you can do an alias
alias scribus-ng='LANG=C LC_ALL=C scribus-ng'
in a global file like /etc/bash.bashrc

At least there is a workaround for this bug:
```
sudo apt-get remove scim-qtimm
echo "alias scribus='LANG=C LC_ALL=C scribus'"|sudo tee -a /etc/bash.bashrc
```

If you choose this workaround the message "QInputContext: no input method context available" still apears in the conole...

[http://www.google.de/search?q=scribus+spinbox+broken](http://www.google.de/search?q=scribus+spinbox+broken)
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-October/022111.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-October/022111.html)

---

