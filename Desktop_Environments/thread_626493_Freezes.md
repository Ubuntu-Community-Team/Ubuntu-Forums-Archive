---
title: "Freezes"
date: 2007-11-29
forum: Desktop Environments
---

### Post by matthen on 2007-11-29
Hey Everyone and thanks for any help.

I've had a problem the last couple of days with my laptop running Gutsy.

I'm running Compiz-Fusion from the Ubuntu repositories, and that's with Gnome.

The computer will freeze, the cursor can still be moved around with the mouse, but clicking is impossible and the keyboard doesn't work. It seems to be randomly triggered when clicking inside a Firefox window.

Pressing Ctrl+Alt+Backspace does nothing during the freeze.

The only thing which might have caused it I imagine is that recently the laptop was left on and unplugged, and it ran out of batteries and turned off.

Any thoughts as to how to resolve this?

Thanks,
Matt

---

### Post by rax_m on 2007-11-29
I've had this before as well.. it appears that X windows just freezes and not the OS. Instead of rebooting completely, try pressing Alt-SysReq (Prtsc)-K at the same time. 

BE WARNED: This kills all of the processes and restarts X. So this should allow you to log in again without a reboot. 

Sorry, not sure what the cause is. But my money is on it being a firefox bug.

---

### Post by matthen on 2007-11-29
Thanks, I'll do that from now on when it happens.

Still wonder if there is a fix?

M

---

### Post by mjfleck2000 on 2007-11-29
I have had computer freezes the last few days also.  I am running Ubuntu/Gutsy with an Nvidia video card.  If I attempt to run desktop effects, the computer will freeze ... usually within 10 seconds, sometimes it make take a few minutes. 

Note that this is NOT with Firefox running. 

The mouse cursor moves but there is no response to clicks nor to any keyboard input.  I secure shelled in from another computer... it was VERY slow to log in and all commands are VERY slow.  Running "top" shows that Xorg is running at 95+ percent.  I killed Xorg and control is returned to the computer. 

I suspect that either there was an update recently to the nvidia driver or to xorg.

My solution, for now,  was to NOT enable desktop effects.

Mike

---

### Post by matthen on 2007-12-01
Anyone have any ideas as to a solution?

Currently I'm running Metacity instead of Compiz to avoid the freezes.

Any help much appreciated.

Matt

---

### Post by didier on 2007-12-01
the problem is using restricted drivers there is a program out there called envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
its works 
i'm running compiz and nvidia driver with no lock ups.

---

