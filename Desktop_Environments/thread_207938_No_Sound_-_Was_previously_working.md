---
title: "No Sound - Was previously working"
date: 2006-07-02
forum: Desktop Environments
---

### Post by kaptainlange on 2006-07-02
For some reason I cannot get any sound to play from Ubuntu.  To double check the hardware I restarted in Windows and everything checks out.  The only thing I did differently the previous boot where it was working was instead of shutting down I chose the hibernate option to see what it did.  On bootup it never recovered and I had to restart by doing a hard shutdown then booting backup.  Since that point, the sound hasn't worked.

I'd appreciate any help in to where to start looking to diagnose the problem.

---

### Post by Ubuntist on 2006-07-03
Although I've not had that problem under Dapper, I often lost sound under Breezy after hibernating.  In my case, the solution was to open the volume-control panel (double-click the speaker icon), select the Switches tab, and make sure that the analog/digital output box is ticked.

If no analog/digital output box is visible, try Edit|Preferences and then selecting analog/digital output.

---

