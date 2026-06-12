---
title: "Games freeze"
date: 2010-02-21
forum: Gaming &amp; Leisure
---

### Post by MrNatewood on 2010-02-21
Some games sometimes freeze at full screen, which leaves me no other option than a hard, nasty, reset.

Is there any way to kill the game at full screen, something like ctrl+alt+delete in windows?

This is something I really miss in linux and it just seems strange it doesn't exist...

---

### Post by MindFusion on 2010-02-21
I get this too, this might be the cause that you have a malfunctioning audio/video driver.

---

### Post by themusicalduck on 2010-02-21
Best way to kill a process when in full screen is to use ctrl+alt+f1. Then login. Use the command ```
top
``` to get you a list of running programs and then ```
killall *nameofprocess*
``` will hopefully kill it. Afterwards press ctrl+alt+f7 to get back to Ubuntu.

If that doesn't work. Try ```
sudo service gdm restart
``` (in the virtual console again) this will kill all running process and reload your desktop. (but you'll lose anything else that was open)

If all else fails.. use ctrl+alt+sysrq+R+E+I+S+U+B.. that will reset the computer in a safer way than just doing a hard reset. Using the restart gdm command will work most times though.

---

### Post by MrNatewood on 2010-02-21
Thanks, that console trick works.

---

