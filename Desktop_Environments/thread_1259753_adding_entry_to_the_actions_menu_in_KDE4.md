---
title: "adding entry to the actions menu in KDE4"
date: 2009-09-06
forum: Desktop Environments
---

### Post by richard.e.morton on 2009-09-06
Hi

I am trying in vain to add a custom action in the context menu for Dolphin. 

I have added this file

/home/richard/.kde/share/kde4/services/convertfiles.desktop

containing:

[Desktop Entry]
Type=Service
Version=2.4.3
Encoding=UTF-8
Icon=kgpg
Actions=ConvertFiles
ServiceTypes=KonqPopupMenu/Plugin,all/allfiles
X-KDE-Priority=TopLevel
X-KDE-Submenu=&Convert Files
X-KDE-Submenu[de]=Convert Files
#X-KDE-Submenu[xx]=Your string 'xx' is the country abbreviation

[Desktop Action ConvertFiles]
Exec=CONVERTDIRECTORY=$(dirname """$U""") && cd """$CONVERTDIRECTORY""" && CONVERTFILE=$(basename """$U""") && OUTPUTFILE=${CONVERTFILE//.${CONVERTFILE#*.}/.svg} && uniconvertor $CONVERTFILE $OUTPUTFILE
Icon=accessories-text-editor
Name=Convert to SVG
Name[de]=Convert to SVG
#Name[xx]=Your string 'xx' is the country abbreviation


The menu appears with the correct entry and clicking on it initiates something which errors with:

Could not find the program '$U)'

However the command I am asking to be executed works in bash:

CONVERTDIRECTORY=$(dirname """$U""") && cd """$CONVERTDIRECTORY""" && CONVERTFILE=$(basename """$U""") && OUTPUTFILE=${CONVERTFILE//.${CONVERTFILE#*.}/.svg} && uniconvertor $CONVERTFILE $OUTPUTFILE

any ideas how I can get this to work?

Thanks in advance
R

---

