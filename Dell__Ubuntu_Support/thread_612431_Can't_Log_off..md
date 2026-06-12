---
title: "Can't Log off."
date: 2007-11-13
forum: Dell  Ubuntu Support
---

### Post by Melissa Lane on 2007-11-13
Hi all, 

Recently put Ubuntu 7.10 on my Dell. For some reason when I go to shut down, I can't. End up having to restart or turn off at the switch. Keep getting the messages:

"libhal shutdown failed - connection closed"

"nm_dbus_signal_device_status_change: assertion 'cb_data ->dbus_connection' failed."

And: "Make sure the message bus daemon is running."

As I'm only days old to Linux, I have no idea what this means nor how to correct it.

Has anyone else dealt with this? And can anyone offer me some words of advise?

Cheers, Mel

---

### Post by Dellfan on 2007-11-14
This likely has to do with ACPI... Two possible solutions:


(1) First see if the the acpi=force kernel option parameter solves your issue

Reboot your pc, after bios messages, when you see the Grub row press ESC key
Select the kernel row and press edit select
Select the "kernel /boot/......" row and press "e" to edit this row
add the acpi=force parameter at the end of the row
then press "enter" and then press "b" to boot

If this works

To make this "acpi=force" kernel boot parameter permanent

Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo gedit /boot/grub/menu.lst

give your user password when requested, you don't see nothing when you type it, then press enter.

Search your default kernel option
# defoptions=nosplash locale=it_IT

and add at the end of the row the
acpi=force
parameter

save and exit

Then to update Grub type
sudo update-grub

(2) If this did not solve your issue, reverse the changes and try 

sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Restart. On "Shutdown" it should.

---

### Post by Melissa Lane on 2007-11-14
Fantastic. Will do.

Thanks Dellfan.

---

