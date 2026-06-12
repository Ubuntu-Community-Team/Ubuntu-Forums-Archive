---
title: "Errors on booting Ubuntu"
date: 2005-04-28
forum: Desktop Environments
---

### Post by FeJaOr on 2005-04-28
I have this kind of errors when ubuntu is loading and don't know what they exactly are...I asked in the chat rooms about it and did what they told me to do and still getting them. They appear after Uncompresing Linux...OK, booting the kernel

pnp : PnPACPI:METHOS_NAME_ _CRS failure for PNP0C01

pnp : PnPACPI:METHOS_NAME_ _CRS failure for PNP0C02

On the chat rooms they told me to change the plug and play option of my bios and I had the same errors after I disable the plug and play.
Anyone who can help me with this?
Thanks

---

### Post by nad on 2005-04-28
At the boot menu selection screen (grub), press the 'e' key to edit the default boot line command. Highlight the long line by choosing it with the up and down arrows keys and press 'e' again. Now add: acpi=off  . Press the enter key use this option at this boot. Press 'b' to boot the computer and watch your messages.

If this solves this problem, edit the file /boot/grub/menu.lst as the superuser. To the line that begins: # kopt=root=/dev/...  add: acpi=off. Now issue the command: update-grub  and this option will automatically be added to your boot entries.

---

### Post by FeJaOr on 2005-04-28
The only lines I got once I press e on the grub are these:

root (hd0,4)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hdas ro quiet splash
initro /boot/initro.img-2.6.10-5-386
savedefault
boot

I couldn't find the lines that are causing the problem 
Thanks

---

### Post by nad on 2005-04-28
What you wish to do is add acpi=off to the second line. Use the arrow keys to highlight the second line and press 'e' again to edit it. Add acpi=off to the end of the line and press the enter key. Now press the 'b' key to boot your computer this time with this option.

---

### Post by FeJaOr on 2005-04-29
After I did what you told me to, the lines dissapeared but today, when I boot ubuntu they came back again!!
I followed exactly the instructions you gave me on adding acpi=off on the kernel /... line in grub and also did the gedit /boot/grub/menu.lst and on the · kopt=root=/dev/... line I added acpi=off and update-grub after all those modifications.
Thanks

---

### Post by nad on 2005-04-29
Please post your file /boot/grub/menu.lst .

---

### Post by FeJaOr on 2005-04-30
I think I figure it out, the problem was that I changed acpi=0 to acpi=off and some erros came up on boot and stuff...but I already changed that and have acpi=0 and acpi=off in the same line and seems to be working.
Thanks

---

