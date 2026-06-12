---
title: "xorg.conf read-only, can't boot, can't fix."
date: 2009-04-11
forum: General Help
---

### Post by Alyn on 2009-04-11
OK, I made some changes to the xorg.conf file, I know what's wrong with it, but I can't save my changes.  I did back it up before changing it, but I can't swap for the backup.

Basically, when I try to boot up the computer I get the following message:


[INDENT][COLOR="Red"]*[/COLOR]An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed in maintainane mode with the root filesystem in read only mode.
[COLOR="red"]*[/COLOR]The root filesystem is currently mounted in read-only mode.  A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell.[/INDENT]

Then the usual command line.  I can open the xorg.conf file to edit and see the error in it (some of the " symbols are replaced by a series of diamonds, probably because I copied and pasted them from the net), but when I try to save the file it tells me I can't because it is read only.  I get the same if I try to replace the file with my backed up copy.

What do I do?

---

### Post by taurus on 2009-04-11
How about running the fsck of your root partition at the prompt?

```
fsck /dev/sda1
```
Assuming /dev/sda1 is where / is.

---

### Post by Alyn on 2009-04-11
Edit: This time it gave me the option to restore graphics settings to default, chose that option, problem solved, now boots up fine.

Thank you so much Taurus.

-------------------
Pre edit post:

OK, thank you Taurus, I'm a step further now, I can boot up but I get the message:

[INDENT][SIZE="4"]**Ubuntu is running in low-graphics mode**[/SIZE]

The following error was encountered.  You may need to update your configuration to solve this.

(EE) problem parsing the config file
(EE) Error parsing the config file[/INDENT]

Using low-graphics mode I have corrected the error in the xorg.conf file but now I still get this every time I boot up.

---

### Post by taurus on 2009-04-11
So you went back to the original /etc/X11/xorg.conf?  See if you need to reinstall a driver for your graphic card in System -> Administration -> Hardware Drivers.

---

### Post by Alyn on 2009-04-11
Don't think I do, I'm using Easy Peasy, based on Intrepid Ibex, but for netbooks, particularly the Asus EeePC, which is what I have, so the default should be fine.  Everything seems to be working fine so far.

When I go to System -> Administration -> Hardware Drivers it just says "No proprietary drivers are in use on this system."

---

### Post by ajgreeny on 2009-04-11
Try starting recovery mode (if easy peasy has it available) and choose xfix from the menu that appears.  It should detect your hardware again as it did at install.

---

