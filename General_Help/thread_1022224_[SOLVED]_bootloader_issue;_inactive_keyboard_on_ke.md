---
title: "[SOLVED] bootloader issue; inactive keyboard on kernel selection"
date: 2008-12-26
forum: General Help
---

### Post by zouberman on 2008-12-26
hi everyone,

i am facing a weird problem and since google does not seem to be a good friend - at least tonight - i have to bug you people.

a couple of months back i formated my desktop computer and clean installed ubuntu 8.10 on it.

this week i decided to install the real time kernel via synaptic and i think i succeeded.

(i thought) i only had to enable the bootloader menu on startup.

approach #1

edit menu.lst manually (uncommented "#hiddenmenu" and # howmany=all)

approach #2

restored the original menu.lst file, installed StartUp-Manager and enabled the bootloader menu using the GUI.

both attempts have the same side effect; after reboot i end up with the bootloader menu list displaying all available kernels (plus the newly installed real time kernel) and an inactive keyboard (?1?) that means that i am not able to select a different kernel other than the default; actually not even the enter button is functional, so i have to wait for the bootloader to time out to login to ubuntu!

after that everything is perfectly normal. suggestions anyone?

---

### Post by zouberman on 2008-12-27
hi there,

seems google is my friend again :)

fyi -> supposedly you own a usb keyboard; just enable "enable legacy settings for usb" on the bios and the keyboard will be alive again the next time the bootloader kicks in.

---

