---
title: "file manager does not recognize .deb file"
date: 2009-03-07
forum: General Help
---

### Post by mattix on 2009-03-07
Hello . I'm a newbie who set up breezy badger (ubuntu 5.10) on a computer I found on the side of the road . After trying to set up my wireless usb adapter and failing , I shelved it . Fastforward to this week . I thought I would take a swing at it again . I downloaded a "wine" package , but when I tried to open it by clicking on it , the file manager window appeared with a message saying " cannot recognize archive type " . The extension on the file is .deb . I tried it through terminal and got a processing error message . Am I missing another package ? From what I can glean from forums and websites I need ndiswrapper and wine  . I just don't know how to run/configure any of this stuff . The computer is an AMD processor with VIA chipset . My adapter is the usb D-link WUA-1340 . Would installing the latest ubuntu clear up any of these issues ? Help me escape the clutches of microsoft once and for all !

---

### Post by scragar on 2009-03-07
Right click, open with, custom command:
```
gdebi
```
Try that.

---

