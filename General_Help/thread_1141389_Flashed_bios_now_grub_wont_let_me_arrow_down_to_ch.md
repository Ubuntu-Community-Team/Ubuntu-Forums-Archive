---
title: "Flashed bios now grub wont let me arrow down to choose Vista"
date: 2009-04-28
forum: General Help
---

### Post by Slovak on 2009-04-28
How do I fix it? All grub entries are still the same and there, I just can't arrow down to choose anything than the default 9.04 kernel, what gives? I flashed the bios through Vista.

---

### Post by jwbrase on 2009-04-28
It sounds like your new BIOS isn't picking up your keyboard.

---

### Post by coffeecat on 2009-04-28
Is it a USB keyboard? Some BIOS's default to USB keyboard disabled. Perhaps the BIOS settings went back to default when you reflashed. You'd think that these days they would be default to enabled. Ah well. If you have a PS2 port on your keyboard, plug a PS2 keyboard in to get into the BIOS and change the settings.

The reason why Ubuntu is responding to the USB keyboard is because it has USB keyboard drivers. At the grub menu stage you're relying on the BIOS picking up keyboard input.

---

### Post by Slovak on 2009-04-29
That was it, bios defaulted to fail safe after the update, once I reset all in there it booted to windows.

---

