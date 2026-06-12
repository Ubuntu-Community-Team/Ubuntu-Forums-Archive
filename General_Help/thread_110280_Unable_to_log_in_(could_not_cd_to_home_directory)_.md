---
title: "Unable to log in (could not cd to home directory) - system broken?"
date: 2005-12-30
forum: General Help
---

### Post by Wermut on 2005-12-30
**Problem:** When booting, the boot splash shows up and everythings seems fine; however, at the end of the boot process the console login screen on vt1 shows up. Trying to login produces the error "unable to cd to home directory". I have not activated the root account, so I'm locked out.

**Background:** I was compiling and installing a program (Battle for Wesnoth, this should not matter). I used checkinstall. So I executed "checkinstall -D make install". I realized I forgot to prepend sudo, hit <ctrl>+<c> and exectued it again with sudo prepended. There were some problems, so I wanted to remove the directory with the sources and try the whole process again. But the bash could not find the command rm. Then the Gnome panels disapperead. I got nervous ant wanted to execute reboot -- command not found. Nothing worked, the Gnome panels disapperead and I got nervous. I switched to vt1 and hit <ctrl><alt><del>. Now I'm trapped as described above.
I don't think that this matters, but the programs running in the background were nautilus, amule and firefox (maybe pan and evolution, don't remember).

**Some more irrelevant information (for the sake of completeness)**
Version: Breezy 5.10
Machine: Samsung X20 notebook
No custom kernel or similar specials

Any help would be appreciated.

---

### Post by sciurus on 2005-12-31
Boot up a live cd, mount your partitions, and assess the damage.

---

