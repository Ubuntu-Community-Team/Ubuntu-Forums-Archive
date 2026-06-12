---
title: "WUBI install would not start..."
date: 2009-03-25
forum: General Help
---

### Post by amadeus266 on 2009-03-25
For anyone who has done a WUBI install and found that it would not start for an unknown reason, I found this out and figured I would share.

Today, I went to restart my computer into Ubuntu after one of my kids had to use it in windows. The computer rebooted and presented me with the boot menu, I selected Ubuntu. Ended up at a prompt instead. No login  just a prompt. I typed reboot and the same thing happened again. After several tries, I instead chose to load windows and that's when I figured it out. Windows did not shut down correctly. Chkdsk ran automatically and windows booted. I then rebooted the machine again and chose Ubuntu. Everything loaded fine and was back to normal. Testing my theory, I restarted the machine again and interrupted windows startup. Same thing happened again, Ubuntu wouldn't start up. Restarted into windows, got the screen that says windows didn't start up correctly, loaded windows, restarted again into Ubuntu and no problems. :popcorn:

---

