---
title: "Amarok MySQL help please"
date: 2006-08-28
forum: Desktop Environments
---

### Post by citizenkeith on 2006-08-28
Running dapper. Just upgraded to Amarok 1.4.2, built from source, and following the directions for installing with MySQL support:
[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

I deleted ~/.kde/share/apps/amarok.

I start up Amarok, go to Configure Amarok, and I'm supposed to click on Collection and choose MySQL from the dropdown menu. But there is no dropdown menu. No mention of database at all.

I'd try the firstrun wizard, but I have no idea how to start that. I don't see any menu item for it.

HELP! ](*,)

---

### Post by citizenkeith on 2006-08-28
I just tried starting over... I ran configure --enable-mysql. After it finished, I got this message (emphasis mine):

>  = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - libvisual Support
 =   - XMMS Visualization Wrapper
 =   - **MySql Support**
 =   - Postgresql Support
 =   - Konqueror Sidebar
 =   - MusicBrainz Support
 =   - MP4/AAC Tag Write Support
 =   - iPod Support
 =   - iRiver iFP Support
 =   - Creative Nomad Jukebox Support
 =   - MTP Device Support


What am I doing wrong??? MySQL is installed already....

EDIT:

Nevermind... I didn't see this one.

>  = mysql_config could not be found, this means that support for MySql
 = will be disabled.


Now I just have to figure out how to install mysql_config. :D

---

