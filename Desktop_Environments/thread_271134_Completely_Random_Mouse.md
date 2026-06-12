---
title: "Completely Random Mouse"
date: 2006-10-04
forum: Desktop Environments
---

### Post by RichLouth on 2006-10-04
I've had this problem for nearly a year now and no amount of forum scouring seems to come up with an answer. Ever since Hoary my mouse, at seemingly random times, decides to move randomly about my desktop. It helpfully opens 20 or so wastebasket windows, or sticks itself to the top right hand corner until I press the esc key, or moves the top panel to the bottom, or opens up every link in my rss feed, or scrolls to the bottom of a page with wild abandon, or any of a number of anoying things.

I really have no idea why this happens. I have an ordinary 3 button/wheel ps/2 mouse.

Some sessions it doesn't happen at all but others it persists to the point of madness. Has anyone else experienced this?

---

### Post by kelt65 on 2006-10-04
Please post the "InputDevice" section for your mouse from /etc/X11/xorg.conf.

Have you tried setting the protocol to "Auto" ?

Turn gpm off as well to see if that is a problem.

---

### Post by RichLouth on 2006-10-04
Thanks kelt65.

Tried changing to auto. Still does it:(

I don't think gpm is installed or on.

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by kelt65 on 2006-10-04
Hey,

In my /var/log/Xorg.0.log I have:

```

(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Logitech Optical Wheel Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Logitech Optical Wheel Mouse: ps2EnableDataReporting: succeeded



```

What do you have?

Try turning gpm off for now while running X - does that help?

---

### Post by RichLouth on 2006-10-04
Sorry to sound stupid. But how do I turn off gpm?

---

### Post by RichLouth on 2006-10-04
I'm fairly certain I don't have gpm.

After trying:

> /etc/init.d/gpm stop
bash: /etc/init.d/gpm: No such file or directory

> grep -R "gpm" /etc/init.d
richard@a-5:~$ grep -R "gpm" /etc/init.d
/etc/init.d/console-screen.sh:    # Inform gpm if present, of potential changes./etc/init.d/console-screen.sh:    if [ -f /var/run/gpm.pid ]; then
/etc/init.d/console-screen.sh:  kill -WINCH `cat /var/run/gpm.pid` 2> /dev/null

And
> ps -A | grep "gpm"
gives me nothing.

Also in grub I've tried adding the kernel options psmouse.proto=imps but it wasn't reckognised. And also added acpi=off apm=off but the problem still persists.

I'm think I might just get a new mouse and see if it isn't just something to do with the hardware.

---

