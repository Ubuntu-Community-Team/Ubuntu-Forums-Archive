---
title: "initramfs"
date: 2009-04-23
forum: General Help
---

### Post by Qbazic on 2009-04-23
I was wondering if anyone could give me some input on how to set up boot arguments after xubuntu has all ready been installed on a computer that will run off the live cd? works fine running off live cd, but once the boot process starts after the installation it does not recognize the Bios date and prompts me to set enable acpi=force I have very little cmd experience but will/or should be able to handle a walk through or maybe will be able to configure problem my self if pointed in the right direction. I was actually wondering if there is an F-KEY that will halt the boot process and allow me to set "acpi=force" during the boot process.Any help would be greatly appreciated and if I don't get back to you tonight I will respond since I'm getting better at forum skills.

thanks Q

---

### Post by DagMan on 2009-04-23
I'm not sure if I'm clear, but I think you're saying you installed xubuntu from a livecd or usb stick and had to use a parameter acpi=force in order to get it to go, and that now you want to do that in the normal install as well?

If this is the case, and the system is not bootable at the moment because of the problem then you can pass the option temporarily to the bootloader. When the computer starts, it will go to grub for a few moments...
Hit **esc** if you can't see the menu.  If you can then skip that part.
Hit **e** (for edit) where you see the selection to boot. Not the recovery mode one but the normal one.
With the line that begins with "**kernel**" highlighted, hit **e** again.
Use the arrrow key to go to the very end of that line, and type in your option... in your case acpi=force or acpi=on or acpi=off or whatever it was that made thing work.
Hit **enter**
Hit the letter **b** to boot.

This only effects the current boot.  When you reboot you'de have to do it agian, so you'd want to add it to the file where the bootloader reads.
type 
**gksudo mousepad /boot/grub/menu.lst**
scroll all the way down and when you see this
**## ## End Default Options ##**
look at all the lines that say "**kernel**" and at the end of them, and be careful as the text may wrap around to be two lines long, add the option you did above.
like this, except mine looks slightly differant,  My big long number is differant after UUID and my vmlinuz is differant, so don't just copy and paste... okay the following is similar to how it would look before editing
```
kernel		/boot/vmlinuz-2.6.28.9 root=UUID=868dca04-0a93-47aa-aa46-0aaa5d243847 ro  single
```
and then  add the option so it looks like this
```
kernel		/boot/vmlinuz-2.6.28.9 root=UUID=868dca04-0a93-47aa-aa46-0aaa5d243847 ro  single acpi=force
```

reboot to test it.

This doesn't fix things for when threre's an upgrade to the kernel.  so go back with the text editor and find a line that says something like further up in the file: 
**# kopt=root=UUID=868dca04-0a93-47aa-aa46-0aaa5d243847 ro**
the big long number after UUID will be differant on yours. Leave that as it is.  All you want to do is add the option to the end of this line so after the ro at the end, put the acpi=force so it looks similar to this
**# kopt=root=UUID=868dca04-0a93-47aa-aa46-0aaa5d243847 ro acpi=force**

I've never heard of the force option with acpi.
I hope this what you're looking for, as I wasn't sure, and if not, or in either case, good luck.

---

### Post by plucky on 2009-04-23
Good answer **DagMan** but couple of corrections.

> gksudo /boot/grub/menu.lst needs to use an editor like nano.

The OP is running Xubuntu so the command should probably be ```
sudo nano /boot/grub/menu.lst
``` as Xubuntu doesn't use gedit.Can't remember the editor Xubuntu uses.

Also "acpi=force" is a valid option. It works for me on an older system.

Well done

---

### Post by spiderbatdad on 2009-04-23
gksu gedit /boot/grub/menu.lst
for ubuntu
or
for xubuntu
gksu mousepad /boot/grub/menu.lst
or sudo nano ...
for either

---

### Post by DagMan on 2009-04-23
Thanks guys, I'll edit above.

---

