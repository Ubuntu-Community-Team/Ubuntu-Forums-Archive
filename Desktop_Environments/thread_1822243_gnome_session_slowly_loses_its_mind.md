---
title: "gnome session slowly loses its mind"
date: 2011-08-10
forum: Desktop Environments
---

### Post by jimnasium on 2011-08-10
I'm seeing a perplexing problem on my laptop. After running for varying times, usually several hours, bits and pieces of the session stop working. I lose the ability to move windows or raise them. The top and bottom bars (which I have hiding themselves) won't appear. The mouse pointer moves but mouse buttons no longer work. As I've enabled focus-follows-mouse, I can hover over a window and use the keyboard in that window (but not the buttons).

Once, when things started failing, I was able to briefly restore function by restarting metacity (kill -hup), but only for a couple minutes.

Nothing looks to be logged in .xsession-errors. I'm running 11.04, with gnome.

Maybe this is a x server problem? (using the x.org intel driver) Maybe unrelated, but I've noticed that the server sometimes misses refreshing little rectangles of screen.

I'm grasping - I'd appreciate any suggestions.

---

### Post by jimnasium on 2011-08-11
A little follow-on: I found can restore the mouse button function by plugging into another port. How strange! The mouse doesn't fail completely - the other buttons work, the scroll wheel works, and the pointer works. The left button fails. I'm traveling now, when I get a chance I'll try it with another mouse.

---

### Post by Frogs Hair on 2011-08-11
Did you run an MD5SUM on you installation disc ? It reads like your installation disc may have been corrupt . 

Open the Disk Utility and on the left side select your hard-drive and see if the disk healthy indicator is green . 

[https://help.ubuntu.com/community/HowToMD5SUMa](https://help.ubuntu.com/community/HowToMD5SUMa)

---

### Post by rockfreakinsolid on 2011-08-12
I'm having *very* similar problems (if not exactly the same... am running Natty as well) - Only now, that problems happen after a mere few moments/seconds of powering up... my browser will do odd things (pop up as a full window, but only the upper left-hand 1/4 of the window is showing what the full window should... the remainder of the "full" maximized window shows the desktop wallpaper), the mouse, when hovering over buttons like maximize, minimize and close ('x'), does not wake these up or have any effect when clicking - other buttons such as refresh, back, forward, etc. - will only respond at odd, random times when it freakin' feels like it, etc. 

I *really* hope someone replies to this thread with a solution soon!!  **PRETTY PLEASE**!!

---

### Post by rockfreakinsolid on 2011-08-22
Mmm, yeah... I see this has people stumped... and things are getting worse with this computer... does no-one have an answer here????

---

### Post by travisHAZE on 2011-08-22
I had a similar problem, when booting try loading GRUB up (press and hold SHIFT while booting) and hit 'e' on the first menu option, add noapic nolapic acpi=off (or try variations of these, ie missing apic and lapic, or missing acpi) etc. Try all 3 first.

Add it right after the words 'quiet splash'

Boot up, (F10) and then play with the computer, if it no longer does this open a terminal window (CTRL ALT T) and type 
```

sudo gedit /etc/default/grub
```In the line GRUB_CMDLINE_LINUX add those three boot parameters, it should look thusly:
```
GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"
```Then save and close and go back to the terminal and type
```
sudo update-grub
```It should generate a new grub boot command (basically making it so you no longer need to load GRUB and add the commands each time you boot)

JUST AN FYI: Adding acpi=off will DISABLE any and all power management features on your computer. ACPI is a tool used by computers to control everything relating to power consumption. IE your computer won't sleep. It will still go into screensaver mode, but hey, if your laptop doesn't have ACPI support, you can't use those features anyway.


I had this very same problem, basically everything would work initially, then after about 5-10 minutes, certain peripherals would fail (my touch pad, my wireless mouse, my wireless keyboard, my integrated keyboard, my integrated monitor, etc.) and would require a hard boot to be able to cause these things to function again. And once booted, I'd have 5-10 minutes until it happened again. This solved it.


[_My Thread with this Same Subject_]("http://ubuntuforums.org/showthread.php?t=1789998")

Enjoy your functioning Ubuntu

---

