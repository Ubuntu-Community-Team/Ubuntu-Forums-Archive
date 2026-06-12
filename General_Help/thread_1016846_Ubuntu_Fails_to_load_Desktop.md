---
title: "Ubuntu Fails to load Desktop"
date: 2008-12-20
forum: General Help
---

### Post by karthi_virtual on 2008-12-20
[COLOR="Navy"][FONT="Arial"]Hi,

[FONT="Arial"]I am new to Ubuntu and I have installed Ubuntu using Wubi 8.10. Every thing is fine but after log in , I am getting black screen instead of Desktop.Please anyone help me to sort out this issue.[/FONT]  [/FONT][/COLOR]
[FONT="Arial"]
Regards,

Karthik[/FONT]

---

### Post by Sef on 2008-12-20
What are your system specs, especially your graphics card?

---

### Post by karthi_virtual on 2008-12-21
[FONT="Arial"]I have installed same on drive E:(total space of 20 GB. While Installing I have selected 15 GB). My system has integrated graphics card (**P4 - Intel - 845 GVSR chip set - 64MB integrated graphics card**). [/FONT][COLOR="Navy"][/COLOR]

---

### Post by abn91c on 2008-12-21
> **karthi_virtual said:**
> [FONT="Arial"]I have installed same on drive E:(total space of 20 GB. While Installing I have selected 15 GB). My system has integrated graphics card (**P4 - Intel - 845 GVSR chip set - 64MB integrated graphics card**). [/FONT][COLOR="Navy"][/COLOR]
compiz has a known bug with intel 845 series cards and ubuntu 8.10 you will have to remove compiz
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by karthi_virtual on 2008-12-23
[FONT="Arial"][COLOR="Navy"]Fine.:([/COLOR][/FONT]

---

