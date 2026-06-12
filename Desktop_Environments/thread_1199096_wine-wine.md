---
title: "wine-wine?"
date: 2009-06-28
forum: Desktop Environments
---

### Post by Syro on 2009-06-28
I installed uTorrent recently with Wine but unintalled the application shortly afterward due to complications.  After removing uTorrent, I also removed Wine from my computer.

My problem is that a shortcut to uTorrent under the Applications->Wine refuse to disappear.  I used Main Menu to delete the uTorrent shortcut but it did nothing to it.  I located the uTorrent shortcut leading to a folder named ".wine" and deleted it hoping it would get rid of the uTorrent shortcut, still no luck.  I'm out of ideas, help me.

---

### Post by gjoellee on 2009-06-28
This is a known bug. I am not sure if you can remove the WINE menu, but you CAN hide it! Just right click on the menu applet on the panel, and select "Edit Menu". You should figure out the rest yourself :p

---

### Post by izizzle on 2009-06-28
In a terminal type ```
alacarte
``` Navigate to the wine section and then to utorrent and delete the entry.

---

### Post by Syro on 2009-06-28
@gjoellee: Aye, hiding works, but it's so annoying to know it's still there...I was hoping to remove it completely.

@izizzle: I've tried deleting it already, but it refuse to be deleted.

---

### Post by Mia1990 on 2009-06-28
Delete the entire wine folder then go to synaptic and remove wine reboot then if you want you can reinstall wine that was the only way i could autocad off my computer [here]("http://ubuntuforums.org/showthread.php?t=1194736") is my post and it fixed mine.

---

