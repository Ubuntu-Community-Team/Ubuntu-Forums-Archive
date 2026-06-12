---
title: "netgear wireless"
date: 2005-12-19
forum: General Help
---

### Post by treehopper29 on 2005-12-19
I'm a noob to lynex and have a both a netgear router and wireless card i just need a step by step how to on setting up my wireless. thanx

router:MR814V2
card:32bit PCI WG311

---

### Post by peterbrowne on 2005-12-19
turn off computer, install card, start computer
run gnome-terminal and now do use the lspci command
post results here

EDIT: According to google it's either Atheros or Prism 54 based (i wanted the lspci to find out that)
so, install the card, start computer - change network applet settings (picture of 2 computers at top-right of screen, settings changed by right clicking on it and clicking prefrences) the interface/card should be changed to ath0 (you have to type in ath0).  What does it say? no such device, or disconnected?  if "Disconnected" install wpasuppliment (gnome-terminal, sudo apt-get instal wpa wpasupplicant) and now install GTKWiFi and your wifi is setup - it is shows no such device, then post results of lspci here

---

### Post by treehopper29 on 2005-12-19
couldnt find network applett settings (wasnt in top right) but here is the results of lspci

0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (r ev c3)
0000:00:08.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
0000:00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Inter face
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c2)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

---

