---
title: "Screen brightness, xubuntu, rc.local"
date: 2013-09-06
forum: Desktop Environments
---

### Post by David_Abergel on 2013-09-06
Hi all.

I currently have the following line in my rc.local which is supposed to set the screen brightness when my laptop boots up:

 echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness

(Note that when I run this command from a terminal, it behaves as expected, so I don't think the issue is with the command itself.)

When X starts, I notice that the brightness starts at full, flicks down (which I assume is the affect of the line in rc.local), and then flicks back up to full. I assume this last change must be some other script which is resetting the brightness.

Does anybody know what this might be or how I should get the brightness to be set to the level I want?

I'm running xubuntu 12.04.

Thanks.

---

### Post by pololo on 2014-03-14
To set the level of brightness you want to see after a start, 
     	 	 	 	   1. put the desired level of brigntness with Fn-keys or other method
2. verify the value you have into /sys/class/backlight/acpi_video0/actual_brightness
3. change the value 9 you have into rc.local for the value obtained in step 2, for that:
- open a terminal for edit the rc.local file -> sudo gedit /etc/rc.local (gedit is my text editor)
- change the value 9 for the value obtained in step 2 (xx):
- be sure that the modified line "echo xx | sudo tee /sys/class/backlight/acpi_video0/brightness" is before the "exit 0" line
- save, close the terminal and restart.

works for me; Asus 1001px, xubuntu 12.04 LTS

---

