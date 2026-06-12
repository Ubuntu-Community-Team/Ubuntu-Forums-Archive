---
title: "Gnome Power Mangement settings do Nothing ?"
date: 2006-07-06
forum: Desktop Environments
---

### Post by orb9220 on 2006-07-06
](*,) 

Every 10 mns. My monitors go blank, green light then 10 mins later to yellow And have to move mouse to turn back on.

Screensave disabled unchecked when idle, "This Works"

Gnome-Power mangement applet Settings:

Put display to sleep when computer is inactive for: Never
Put Computer to sleep when  it is inactive for: Never

On General tab have Do Nothing on both

Note: It has no effect if I change the slider from 1min. to never.
      My monitors blank with green lights on but screens blank out.

I have even tried by disable Gnome-Power from starting up at boot. 
But still have monitors turning off.

Bios AC power is set for Off I assume that is mangement. Older System.
Tried with on no effect from Bios.

Nvidia FX-5200 with nvidia drivers on dual monitors.

:-k  Is there anyway I can track what process is doing this? 

I am new to tracking this down thru Logs? Running a cmd or check configs. 

Just need info on where to look and what to run to track this down.

Could the display Drivers? or xServer itself be doing this?

Any help greatly appreciated since this is my last major issue to
having everything setup the way I like.  

It's been 4 days now and I havn't been back to my XP DARK! side :evil:  since.

---

### Post by orb9220 on 2006-07-07
o

---

### Post by wpshooter on 2006-07-07
Try this.

Set your screen saver ON to 1 minute.

Set your power management/screen blanker to 3 minutes.

Let screen saver kick in, let power screen blanker kick in.

Move mouse.

Restart machine.

Then uncheck screen saver (do NOT move slider) and see if just screen blanker will kick in after 3 minutes.

Move mouse to bring screen back on.

Move screen blanker to NEVER.

Wait to see if it goes blank.


P.S. - this is what worked for me, but don't ask me why.

---

### Post by orb9220 on 2006-07-08
Nope seems to be a problem in gnome-power mangement. [-X 

I finally got it to work right by running gconfig from system tools

and manually setting the AC_ stuff to 0 for disabled i guess

Now works like a champ.

Concered that Ubuntu would install a control applet that is obvious that it is having tons of issue's especially with laptops.

---

