---
title: "Gnome ShortCuts"
date: 2006-07-20
forum: Desktop Environments
---

### Post by redbass on 2006-07-20
I have a 3 years old ASUS laptop (L3000 series), with Ubuntu Dapper install on. 90% of drivers work well, but the hot keys of asus (for be clear, the volume, play, stop keys,...) don't wont to do nothing. 
I try to analize the signals of ACPI with ACPI_LISTENER, and de deamon work. Then I analizi the /etc/acpi/events and the script it's ok (the key code is the same). At last i try to exec the script of ACPI suggest from the event script (/etc/acpi/volumeup.sh or something like that) and nothing happen.
What is the problem?
What is the comand of Gnome for rise up the volume and show the pup-up of volume?

P.S. at last i can say thet i prepare a script for switch from CRT2 to CRT1 in clone mode, i use Hotkays of ASUS, and all works good.

---

### Post by fabiand on 2006-07-20
Hey,

did you try to use the keyboard shortcuts tool in System -> prefernces?

---

### Post by redbass on 2006-07-21
Yes, but the editor can't take the hotkey of ASUS.

this is my */etc/acpi/events/asus-volume-up* code

```
event=hotkey HOTK 00000030
action=/etc/acpi/volupbtn.sh
```
Today i have modified the volupbtn.sh, and i have write 
```
gedit
```
for run... the homonym program... and it work.

WHY THE GOME VOLUME DON'T WONT WORK??????????

---

