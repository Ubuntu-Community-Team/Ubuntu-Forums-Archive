---
title: "vmplayer vmware turn on virtual machine"
date: 2006-11-30
forum: Desktop Environments
---

### Post by Joe_CoT on 2006-11-30
I've tried multiple guides, with both vmplayer (the repo version and the newest version), and vmware server.

After setting up the virtual machine (for either windows xp or windows 2000), and running the virtual machine, it hangs at a blank screen. Tried this with vmplayer. After getting frustrated with it, i installed vmware server, setting up the virtual machine through its gui. Same effect. I originally thought that the VM was unable to mount my iso, or cd-rom drive, or floppy image; according to the vmware server, the VM never made it past the "powering on" stage. Other people seemed to be having this problem, and the answer was removing libdbus-1-2; i have no such package, and even exported the 1.3 version. No luck. Sits there, taking up 100% cpu, indefinately.

Any help would be appreciated.

---

