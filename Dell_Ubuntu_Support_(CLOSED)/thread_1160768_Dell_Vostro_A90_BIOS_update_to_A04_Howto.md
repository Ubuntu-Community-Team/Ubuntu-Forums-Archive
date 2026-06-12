---
title: "Dell Vostro A90 BIOS update to A04 Howto"
date: 2009-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tazforky on 2009-05-16
Just posting how I updated the Dell Vostro A90 BIOS from factory shipped A03 to A04 without using a bootable USB key.

Assumes:  Dell Diagnostics partition still exists in /dev/sda1 and Ubuntu is installed on /dev/sda2

Risks: Completely at your own, but these steps worked for me


[LIST=1]
[*]Download Dell BIOS A04 (STA04DOS.EXE) from support.dell.com, specifically: [http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=306454](http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&~mode=popup&file=306454)
[*]sudo su -
[*]mount /dev/sda1 /mnt
[*]cd /mnt
[*]cp autoexec.bat autoexec.save
[*]echo "C:\COMMAND.COM" > autoexec.bat
[LIST=1]
[*]You probably could just "C:\COMMAND.COM /C STA04DOS.EXE", but it seems safer to just goto DOS in case you forget to undo the autoexec.bat file.
[/LIST]
[*]cp (download_path)/STA04DOS.EXE /mnt
[*]cd /
[*]umount /mnt
[*]reboot
[*]Press "0" to stop at Dell's Boot Menu
[*]Select "Diagnostics" which boots the Dell Diag partition, the modified autoexec.bat and drops you to a DOS shell.
[*]Make sure the AC plug is powering the Vostro
[*]STA04DOS.EXE
[*]Wait for the program and the auto-power down / reboot that occurs
[*]At this point you can either boot back to the Diagnostics DOS prompt and move back the autoexec.save to autoexec.bat or boot to Ubuntu, mount /dev/sda1 and do it from there.
[/LIST]
Enjoy.

---

