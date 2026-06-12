---
title: "Gnome: Screws up my time??"
date: 2007-10-27
forum: Desktop Environments
---

### Post by Guardian-Mage on 2007-10-27
This may not be a problem with GNOME but oh well. I am dual booting Ubuntu 7.10 Gutsy with Windows XP Home. Now whenever I restart my computer my time for Ubuntu and Windows Screws up. I've had this problem with Windows before and I don't use windows so I don't care, but It is annoying with GNOME. I have my time zone set to America/Halifax and config set to manual(I can't figure out automatic><) and it randomly adds 3-8 hours onto my clock. What is going on??

---

### Post by Spare Tire on 2007-10-27
I have the same problem. I think i figured what the problem is but i can't figure how to solve it.
I think Ubuntu takes the time of the bios and considers it as GMT, then adds the modifier for your time zone. Windows on the other hand modifies your bios time directly. So everytime you change your windows time to the correct time, ubuntu will then add the modifier to it. I'm in Montreal timezone and ubuntu just displays -4h to that.

---

### Post by Rui Pais on 2007-10-27
Hi,
try edit the file /etc/default/rcS changing
UTC=yes to UTC=no

hth

---

### Post by johnny9794 on 2007-10-27
Whats your bios time set on?

Set bios time to correct timing and make sure the motherboard battery is "ok"

---

### Post by destineal on 2007-10-28
I had the same problem. I fixed it by:

1. putting the mouse cursor on the time.
2. Right click
3. _P_references
4. Make sure Use _U_TC is checked
[img]http://www.oldsconnection.com/forum/album_pic.php?pic_id=1249[/img]

---

### Post by Spare Tire on 2007-10-29
Thanks, that fixed my problem.

---

