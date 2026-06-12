---
title: "teamviewer 8 quicksupport"
date: 2014-03-17
forum: Desktop Environments
---

### Post by cccc on 2014-03-17
hi

Knows anyone where can I download teamviewer 8 quicksupport for Ubuntu?

---

### Post by slickymaster on 2014-03-19
The direct link to download TeamViewer QuickSupport is [http://download.teamviewer.com/download/teamviewer_qs.tar.gz](http://download.teamviewer.com/download/teamviewer_qs.tar.gz) available at [http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

---

### Post by cccc on 2014-03-20
> **slickymaster said:**
> The direct link to download TeamViewer QuickSupport is [http://download.teamviewer.com/download/teamviewer_qs.tar.gz](http://download.teamviewer.com/download/teamviewer_qs.tar.gz) available at [http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

Thx, but howto create a .deb package from [http://download.teamviewer.com/download/teamviewer_qs.tar.gz?](http://download.teamviewer.com/download/teamviewer_qs.tar.gz?)

---

### Post by slickymaster on 2014-03-20
> **cccc said:**
> Thx, but howto create a .deb package from [http://download.teamviewer.com/download/teamviewer_qs.tar.gz?](http://download.teamviewer.com/download/teamviewer_qs.tar.gz?)

_Basically:_
[LIST=1]
[*]Extract source .tar.gz
[*]Run dh_make
[*]Edit debian files
[*]Run debuild
[/LIST]

[HOW TO CREATE A .DEB PACKAGE [UBUNTU / DEBIAN]]("http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html")
[What is the simplest Debian Packaging Guide?]("http://askubuntu.com/questions/1345/what-is-the-simplest-debian-packaging-guide")

---

### Post by cccc on 2014-04-24
Thx, but maybe someone have already **Teamviewer QuickSupport .deb package**?

---

### Post by slickymaster on 2014-04-24
Teamviewer 9 is available now for download, and it introduces quick support for Linux users. You can download it from [here]("http://www.teamviewer.com/en/download/linux.aspx") (TeamViewer QuickSupport is available as a separate app on the same page).

---

### Post by EmpireITtech on 2014-04-24
TeamViewer 9 already has the deb built for you - just download and install >> [http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

*EDIT* Use the [COLOR=#232323][FONT=Arial]32-Bit / 64-Bit Multiarch if you're on 12.04 or later[/FONT][/COLOR]

---

