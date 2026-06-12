---
title: "Disable DPMS from terminal"
date: 2006-01-24
forum: Desktop Environments
---

### Post by jerris86 on 2006-01-24
i suspect one of the above powersaving features are intefering with my lcd display. My screen whites out while im watching dvs/avis. it also whites out when after a when im in the failsafe mode. I suspect it may be due to DPMS or ACPI or Powernowd

Does anyone know how to turn off each of these features?

---

### Post by dogson on 2006-01-24
xset -dpms

---

### Post by jerris86 on 2006-01-24
How do u re-enable it then?

Is the command u listed above permanent? Or do i have to type it each time i start the computer?

---

### Post by dogson on 2006-01-24
if you are using gnome i think you can disable it in the screensaver settings if you want to disable DPMS permanent for X you need to edit /etc/X11/xorg.conf and put a # before the line Option  "DPMS"

---

### Post by jerris86 on 2006-01-24
When u say disable from screensaver setting, do you mean unchecking the display power management. It didnt work and i tried to enable it and move the 3 options to 0. In kubuntu, i can disable it but in ubuntu i can only drag it to 0.

How do i edit xorg.conf? Can u provide details? Newbie here.

---

### Post by jerris86 on 2006-01-24
I tried "sudo kate /etc/X11/xorg.conf" from terminal.

Warning: unknown mime-type for "/etc/X11/xorg.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
jerris@ubuntu:~$ sudo kate
jerris@ubuntu:~$ sudo kate /etc/X11/xorg.conf
Qt: Locales not supported on X server
Error: "/var/tmp/kdecache-jerris" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
Error: "/tmp/kde-jerris" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
Error: "/tmp/ksocket-jerris" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2

and kate opened the file called "xorg.conf" and i get this
------------------------------------------------------------------------
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection
------------------------------------------------------------------------

are u suggesting i change it to this?
------------------------------------------------------------------------
Section "Monitor"
	Identifier	"SyncMaster"
#	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection
------------------------------------------------------------------------

---

### Post by vayu on 2006-02-21
[QUOTE=jerris86

are u suggesting i change it to this?
------------------------------------------------------------------------
Section "Monitor"
	Identifier	"SyncMaster"
#	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection
------------------------------------------------------------------------[/QUOTE]

Yes put the # in front of dpms to comment it out in xorg.  As far as all the konsole errors with kate, I get the same thing, but kate still seems to work ok.

---

