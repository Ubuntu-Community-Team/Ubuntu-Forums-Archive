---
title: "Where did the Standby (Suspend-to-RAM) Button go?"
date: 2006-05-30
forum: Desktop Environments
---

### Post by Donald on 2006-05-30
Hi all,
there used to be an orange standby (suspend-to-ram) and a blue hibernation (suspend-to-disk) button in the logout menu.
Now the orange standby (suspend-to-ram) button is gone, which is a pitty, because i used this option more often than hibernation, simply because it is faster.
Is it possible to get it back, or instead of the blue hibernation button?

---

### Post by xXx 0wn3d xXx on 2006-05-30
[QUOTE=Donald]Hi all,
there used to be an orange standby (suspend-to-ram) and a blue hibernation (suspend-to-disk) button in the logout menu.
Now the orange standby (suspend-to-ram) button is gone, which is a pitty, because i used this option more often than hibernation, simply because it is faster.
Is it possible to get it back, or instead of the blue hibernation button?[/QUOTE]
Go under System > Prefrences > Power Management and click on the "General" tab. Now, where is says "Sleep button action" select standby. Check under System and click "Quit." The suspend option should be there.

---

### Post by Donald on 2006-05-31
Thank you very much, the orange standby button in the log-out menu is back again.
Standby to RAM works perfectly with my desktop Asus P4P800 SE board.

Hibernation does not work for me, i guess because i use an encrypted swap partition.
It even destroys my grub now and then which i installed in the root partition.
Really do not know why this is.

Is it possible to deactivate the blue hibernation button? Modification of
"/etc/default/acpi-support" does not change the logout energy options.

---

### Post by MrMinute on 2006-05-31
Today I did an upgrade from Breezy to Dapper and the standby and hibernate button is missing as well. I tried your advice but I don't have any "standby" to select in the described location. I can select do nothing ("Nichts tun"), black screen ("Schwarzer Bildschirm") and energy save option ("Energiesparoption"). No standby to select and no standby button. Could the reason be because of "initializing of HAL failed" when logging in to Ubuntu?

---

### Post by Donald on 2006-05-31
MrMinute,

"bei Betätigung des Energiesparknopfes - Energiesparoption" enables the standby button in the logout menu.

---

### Post by jasay on 2006-05-31
[QUOTE=Donald]Is it possible to deactivate the blue hibernation button? [/QUOTE]Try this.  Open gconf-editor and navigate to /apps/gnome-power-manager and "uncheck can_hibernate"

---

### Post by Donald on 2006-05-31
jasay, that worked - at least for the logout menu.

Standby and Hibernation options are still selectable in the login screen GDM
though. Is it possible to deactivate them too?

Is "/etc/default/acpi-support" still used? It seems to me it does not matter if
"ACPI_SLEEP=true" and "ACPI_HIBERNATE=true" are enabled or disabled.

I am just curious how things work, otherwise i can live with that,
dapper runs quite well for me.

---

### Post by MrMinute on 2006-05-31
[QUOTE=Donald]MrMinute,

"bei Betätigung des Energiesparknopfes - Energiesparoption" enables the standby button in the logout menu.[/QUOTE]

Unfortunately it does not. I tried all options but the buttons never showed up in the logout/shutdown dialog.

---

