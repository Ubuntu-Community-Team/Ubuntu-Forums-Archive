---
title: "Goofy Fluxbox freezing issue"
date: 2006-09-13
forum: Desktop Environments
---

### Post by DuplexEmotions on 2006-09-13
Howdy!

I'm having an odd problem with fluxbox. Whenever I try to use the "reconfigure" or "restart" functions (or try modifying the slit orientation, that sort of thing) everything locks up. If I catch it quickly enough I can ctrl-alt-backspace, but only takes a couple seconds to totally lock up.

I installed by going with the ubuntu server install, then installing xorg and fluxbox manually. Haven't had any trouble with the other computers I installed it to. I'm using a 6600GT CO card with the nvidia drivers.

here's the content of my .xinitrc file

fluxbox & wmpid=$!

wmdrawer &

wait $wmpid

any help would be appreciated, especially since I don't know where the log file for the lock up is located.

Thanks!
John

---

### Post by kerry_s on 2006-09-13
How come your useing .xinitrc instead of /.fluxbox/startup? I don't even have a .xinitrc, so i'm guessing you added that. Are you using gdm for your log in manager?

Here's what i use to install mine and never have problems, i just installed on edgy 2 days ago.

apt-get install x-window-system-core fluxbox gdm xterm synaptic

Then i reboot and select fluxbox in session and log in, do some uninstalling of the extra apps then install what i want.

I'm thinking perhaps since you did xorg instead of all the x window stuff, something might have been missed. Is there any thing in your .xsession-errors that might be telling you something. here's what mine looks like->
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "user"
/etc/gdm/Xsession: Beginning session setup...
athcool version 0.3.11 - control power-saving mode on AMD Athlon/Duron CPUs

!!!WARNING!!!
Depending on your motherboard and/or hardware components, 
enabling Athlon powersaving mode may cause:
 * noisy or distorted sound playback
 * a slowdown in harddisk performance
 * system locks or instability
 * massive filesystem corruption (rare, but observed at least once)

Before use athcool, you must recognize these potential DANGERS.
Please use athcool AT YOUR OWN RISK.

athcool is supplied "as is". The author disclaims all warranties,
expressed or implied. The author and any other persons assume
no liability for damages, direct or consequential, which may 
result from the use of athcool.

VIA KM266[A]/KL266/KM333 (1106 3116) found
enabling 'Disconnect when STPGNT Detected' bit ...  done
	Address 0x92 : 0x69 -> 0xE9
enabling 'HALT Command Detection' bit ...  done
	Address 0x95 : 0x1C -> 0x1E
BScreen::BScreen: managing screen 0 using visual 0x21, depth 24
Conky: forked to background, pid is 3774

Conky: desktop window (a2) is root window
Conky: window type - override
Conky: drawing to created window (800002)
Conky: drawing to double buffer

```

---

### Post by DuplexEmotions on 2006-09-13
I don't have a .xsession-errors file.

the reason I use a .xinitrc file is I don't use a graphical login manager, so I run with startx. I installed x-window-system-core , and I've also updated fluxbox to the most recent version (non repos).

Thanks for the help thus far.

edit: it looks like the restart button is working, it's just reconfigure that is giving me issues.

---

### Post by kerry_s on 2006-09-14
That's what i thought. Can you look in /.fluxbox/menu and run the command for reconfigure in terminal and see what errors it gives if any. On mine  the reconfigure button has never worked, i've always changed the .init manually :-?

---

### Post by DuplexEmotions on 2006-09-14
the menu file just redirects to /etx/X11/fluxbox/fluxbox-menu

I don't know what the reconfig command is.

---

### Post by DuplexEmotions on 2006-09-15
I found the problem, it came from a program setting my number of workspaces to 0 in the init file.

thanks for the help!

---

