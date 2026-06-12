---
title: "Lotus Symphony doesn't show-up in menu"
date: 2008-08-30
forum: Desktop Environments
---

### Post by x1a4 on 2008-08-30
Hi,

I installed IBM's Lotus Symphony (productivity suite), but it doesn't show-up in Xfce's menu. So I replaced its launcher with my own, but that doesn't display Symphony either. Other launchers work well. When I change or add one, the changes are recognized at once. What's wrong with this launcher? Thank you.

```

[Desktop Entry]
Version=1.0
Type=Application
Name=IBM Lotus Symphony
GenericName=Symphony Productivity Suite
Comment=Word Processor, Presentation App, Spreadsheet
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.presentation;application/vnd.oasis.opendocument.presentation-template;application/vnd.oasis.opendocument.spreadsheet;application/vnd.oasis.opendocument.spreadsheet-template;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.impress;application/vnd.sun.xml.impress.template;application/vnd.sun.xml.calc;application/vnd.sun.xml.calc.template;application/msword;application/vnd.ms-word-template;application/rtf;application/vnd.ms-powerpoint;application/vnd.ms-powerpoint-template;application/vnd.ms-excel;application/vnd.ms-excel-template;application/vnd.lotus-lwp;application/vnd.lotus-mwp;application/vnd.lotus-prz;application/vnd.lotus-mas;application/vnd.lotus-smc;application/vnd.lotus-1-2-3;application/vnd.lotus-12m
Exec="/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.1.20080602-1703/apps/IBM Lotus Symphony" %U
Icon=/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.1.20080602-1703/icons/symphony32.ico
Terminal=false
Hidden=false
Categories=Application;Office;GTK;
StartupNotify=false
Encoding=UTF-8

```

---

### Post by x1a4 on 2008-09-03
bump
anyone -|

---

### Post by mixmaster on 2008-09-04
Complete shot in the dark.

The exec line is very long, maybe you are tripping over some internal limit.

Create a shell script to start symphony, make sure it works and then create a launcher for the shell script instead.

---

### Post by lwb4007d on 2008-09-04
[font=Times New Roman]**Very good!!!!**[/font]------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU2563439.jpg[/img]Well come to our site:buy [Warhammer Online Gold](http://www.toppowerlevel.net/gamelist.php?fid=3966) [2 Moons Dil](http://www.toppowerlevel.net/gamelist.php?fid=4048)  buy [RS Gold](http://www.toppowerlevel.net/gamelist.php?fid=4011) [SRO Gold](http://www.toppowerlevel.net/gamelist.php?fid=4013) [EVE Online ISK](http://www.toppowerlevel.net/gamelist.php?fid=4044)

---

### Post by x1a4 on 2008-09-05
> **mixmaster said:**
> The exec line is very long, maybe you are tripping over some internal limit.
Already thought of that, and that's not it.  It does show up in other GUIs like LXDE and FVWM-Crystal, so it's probably an Xfce thing.

---

### Post by tdd on 2008-09-09
Maybe you should try posting this in the Linux support forum for Symphony:

[http://symphony.lotus.com/software/lotus/symphony/installForum.nsf/AllDateThreadedWeb?OpenView&RestrictToCategory=Linux](http://symphony.lotus.com/software/lotus/symphony/installForum.nsf/AllDateThreadedWeb?OpenView&RestrictToCategory=Linux)

---

### Post by gramound on 2010-09-07
I just resolved a similar issue with Lotus Notes: add a "TryExec=" line with the path to the same executable as your "Exec" line.

---

### Post by artemis761 on 2010-12-27
I had a similar issue with Lotus Symphony 3.0. The first thing to check is that the application launches via terminal. Use the "symphony" command.

Then edit the Main menu to create a application launcher. The attached screen shot [Lotus.png] shows the properties.

Note: The Application icon [symphony16.png] can be found in:

/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugin /com.ibm.symphony.standard.branding_3.0.0.20101015-2340/icons

---

### Post by artemis761 on 2010-12-27
Attached is a copy of the "IBM Lotus Symphony.desktop" file from the "/usr/share/applications" directory.

---

