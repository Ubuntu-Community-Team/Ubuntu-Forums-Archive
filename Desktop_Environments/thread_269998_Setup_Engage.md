---
title: "Setup Engage"
date: 2006-10-02
forum: Desktop Environments
---

### Post by blamecanada on 2006-10-02
I have recently been trying E17 on Ubuntu/Dapper and love it, and i have decided to try engage. Problem is when i run it, i get a black box on the desktop, and the terminal says 


Esmart_Trans Error: Could not read root window pixmap property!
Esmart_Trans Error: Cannot create transparency pixmap: no valid wallpaper and no background color set.
am a system tray :) :)
File: /usr/share/engage/icons/xapp.eap is not up to date for key "collections/0" - needs rebuilding sometime
You should _really_ create /home/tim/.e/e/applications/bar/engage and populate it
File: /home/tim/.e/e/applications/all/eterm.eap is not up to date for key "collections/0" - needs rebuilding sometime


I really dont know what i need to do to fix this.

---

### Post by Currahee on 2006-10-22
Hi blamecanada, i' m trying to install engage too...
> /home/tim/.e/e/applications/bar/engage and populate it
You should create this directory: ~/.e/e/applications/bar/engage and populate it with **.desktop** or **.eap** icons.
If you want to convert **.eap** to **.desktop** (eap support is really gone on e17):
*eap_to_desktop example.eap*

Sorry for my english...

---

### Post by gottferdamnt on 2006-11-27
> **blamecanada said:**
> i get a black box on the desktop,


Same problem, how can i fix it? I populate my dock already but examine configuration seems to not work.

---

### Post by Currahee on 2006-12-01
> **gottferdamnt said:**
> Same problem, how can i fix it? I populate my dock already but examine configuration seems to not work.
Install libewl1-engines-all... [http://dnnd.netsons.org](http://dnnd.netsons.org)

---

