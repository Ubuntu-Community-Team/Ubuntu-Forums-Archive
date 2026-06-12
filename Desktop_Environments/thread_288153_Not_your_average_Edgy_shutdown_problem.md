---
title: "Not your average Edgy shutdown problem"
date: 2006-10-29
forum: Desktop Environments
---

### Post by fats on 2006-10-29
Hi! I've spent the past couple hours looking for a solution to my problem, but everyone else seems to be having trouble rebooting or shutting down in a different way than I do. When I click on the "Exit" icon at the top-right-hand corner of my screen, *nothing* happens, except everything freezes. I can still move the mouse around, and I can Ctrl-Alt-F1 to a terminal, but if I go back to Ctrl-Alt-F7, the screen is still there, just as I left it. It's as if the screen with all of the options for shutting down / rebooting / etc. has come up, but I can't click on anything (and it doesn't display anything, either). I can't click on anything else.

I have no trouble with "shutdown -h" or "shutdown -r" in the terminal - the problem is just that the exit button has somehow turned into a "freeze my X-Session" button. This didn't happen in Dapper, so I'm sorry if this is the wrong forum to post it in. I'm using Gnome on a P4 processor with an ATI Mobile Radeon video card (in a laptop).

Thanks! :)
Andy

---

### Post by zek725 on 2006-10-31
I have a related shutdown problem since Edgy. Edgy Eft shutdown does not work. Freezes at WILL NOW HALT. Reboot works fine. I've reinstalled Edgy Eft from scratch and this happens. Dapper -> Edgy, it works fine. ](*,)

---

### Post by dheerajsp on 2006-10-31
no problems for me. just works fine. but i still dont know how Suspend works. i dunno what it does!!!

but the top-right-corner button works perfectly.

---

### Post by bluenova on 2006-10-31
Simlar issues on Edgy here (fresh install)

I have my own shutdown script, so to allow non-sudoers to use it, I edited the sudoers file so users can do run 'shutdown -h now' without a password. I set it up exactly the same way in Edgy and it no longer works.

---

### Post by zek725 on 2006-10-31
I've found a solution that worked! :D  [http://www.ubuntuforums.org/showthread.php?t=187186](http://www.ubuntuforums.org/showthread.php?t=187186)

---

