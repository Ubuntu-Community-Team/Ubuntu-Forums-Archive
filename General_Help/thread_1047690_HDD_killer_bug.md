---
title: "HDD killer bug"
date: 2009-01-22
forum: General Help
---

### Post by WannabeFantasma on 2009-01-22
i think i might have that but, i want to try the solution but i don't get what they mean by>>> you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

can someone help me?

---

### Post by WannabeFantasma on 2009-01-23
no one? :(

---

### Post by sedawk on 2009-01-23
Open a terminal and do this

[CODE]
sudo gedit /etc/default/acpi-support
[CODE]

This will open the file (as root) in the editor gedit (so it is writable).
Search the line with ENABLE_LAPTOP_MODE. It should look like this.
[CODE]
ENABLE_LAPTOP_MODE=false
[CODE]

If not (e.g. if there is =yes or =true or similar), change it
to the above "false" value, save the file, restart the computer.

---

### Post by WannabeFantasma on 2009-01-23
aaaah  thats why normal /etc/default/acpi-support didn't work :rolleyes:

TY :)

weird it's allready on false :s

---

