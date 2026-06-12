---
title: "ACPI/APM causing X server to not start?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by sjashton on 2006-09-17
If i power up my machine from cold the xserver will not start, after the initial loading screen i get a blank monitor (save a few flickers) then the monitor goes to sleep (indicated by state LED blinking) for about 30 seconds before it coming back on with a black/white screen divided by a horizontal line for a few seconds and then a login prompt, typing startx doesn't launch the GUI so i have to reboot using re-set switch. This has been happening everytime i start from cold, i thought this was due to any configuration changes i may have made in my last good session so i've been booting into windows getting info from here and other places on the www and applying changes in recovery mode, this morning i recovered my GUI by loading the default xserver, and i found that if i then changed that xserver to match the one i had before (which wouldn't boot) with compiz + Nvidia drivers i could go through 10 re-starts and it will always re-launch the GUI - which makes no sense to me at all. Anyway i turn on the machine this evening and the exact thing happened again - can't launch GUI, i started t think that perhaps my CRT monitor was going into some kind of sleep mode if left not attached to a powered up system for a period time (which may sound like a stange line of enquiry, but things ARE strange). Anyway, i discovered if i boot into into windows then restart and select Ubuntu from GRUB the system fully boots up, so i start to think i may be onto something here, i reckon that all the times i've recovered the GUI it was NOT due to the changes i applied in recovery mode (as well as loading default Xserver on other occaisions i did stuff like update/upgrade, uninstall, re-install Nvidia etc) but the fact that i had booted into Windows to get info then restarted. It seems that i have to get my monitor into a state where it is displaying SVGA and the re-start and i can launch X. I could be wrong i know nothing of monitors but is there some kind of bi-directional communication between a system and a monitor, where the screen shakes hands with the graphical system? If so i assume that ACPI/APM would utilise this and hence amending BIOS settings would correct my booting problems. If i am right in this I think this is very important for new users as i was thinking that updates i downloaded plus compiz/xgl stuff i was doing was causing my problems, I actually went through about 4 formats/clean installs now it looks like all that was needless, also when there flagged posts on here saying stuff like "updates break the xserver" i'm sure you can see where i'm coming from.

If anyone can give me some feedback on my thoughts/theory i would much appreiciate it. In the meantime i'm going to test the theory with a load of restarts, power downs as well as research all stuff in the ACPI section of BIOS setting in the ASUS A8V manual.

Love Ubuntu BTW, compiz blows my mates minds :)

---

### Post by sjashton on 2006-09-17
I,m back, here is the method and results from my experiment.

Since my last session when i posted above -

TURN OFF MACHINE
TURN ON MACHHINE -> GUI DOES NOT LOAD, STUCK AT PROMPT -> SUDO REBOOT
GUI DOES NOT LOAD, STUCK AT PROMPT -> SUDO REBOOT
GUI DOES NOT LOAD, STUCK AT PROMPT -> SUDO REBOOT
GUI DOES NOT LOAD, STUCK AT PROMPT -> SUDO REBOOT
GUI DOES NOT LOAD, STUCK AT PROMPT -> SUDO REBOOT
SELECT WINDOWS FROM GRUB -> TURN OFF MACHINE
SELECT UBUNTU (DEFAULT)FROM GRUB -> GUI DOES NOT LOAD -> SUDO REBOOT
SELECT WINDOWS FROM GRUB -> RESTART
SELECT UBUNTU (DEFAULT) FROM GRUB -GUI LOADS -> RESTART
SELECT UBUNTU (DEFAULT) FROM GRUB -GUI LOADS -> RESTART
SELECT UBUNTU (DEFAULT) FROM GRUB -GUI LOADS -> TURN OFF
SELECT UBUNTU (DEFAULT) GUI DOES NOT LOAD -> SUDO REBOOT
SELECT WINDOWS FROM GRUB -> RESTART
UBUNTU GUI LOADS.

Conclusion; monitor cannot display GUI when starting from cold unless windows GUI is launched first and then system RESTARTED, monitor needs to of displayed in VGA/SVGA mode in any one power up session to launch GUI/xserver.

This is going to cause enormous frustration to any other new users who will assume that updates they have downloaded along with making Compiz work when they first install Ubuntu is causing boot up problems. My monitor is just a regular CRT and ACPI/APM settings are default ones (if these can be amended to correct this problem)

---

