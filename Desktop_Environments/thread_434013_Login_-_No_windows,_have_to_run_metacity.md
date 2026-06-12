---
title: "Login - No windows, have to run metacity"
date: 2007-05-05
forum: Desktop Environments
---

### Post by mythik on 2007-05-05
When I log in, none of my windows are moveable and they don't have the whole "minimize, mazimize, close" frame.  I could still start firefox, terminal, whatever program I needed, it's just that I couldn't move them at all.  

I tried clicking on the "show desktop" button at the bottom left hand corner of my desktop (bottom panel) and I got an error saying something along the lines of my window manager is not found.

So, to get everything to work, I have open up a terminal and type in metacity.

Any ideas on how I can fix this, or at the very least, is there a location where I can tell gnome to run certain commands upon startup (like I used to with msconfig in windows)?

Ubuntu, fiesty fawn.

---

### Post by Outrunner on 2007-05-05
Hmm... I'm not sure since I haven't used Gnome in a long time, but I think the path is System->Preferances->Sessions( then check the last tab)

---

### Post by mythik on 2007-05-05
yeah, wish i could delete this thread.  basically I needed to delete ~/.gnome2/session

....which I found after doing a search on these forums.  I searched before posting..but apparently not with the correct keywords..sorry about that

---

### Post by Outrunner on 2007-05-05
The only important part is that you found your answer :)

---

### Post by cdrom600 on 2007-05-06
I'm having the same problem, but deleting ~/.gnome2/session has no effect.  Has anyone else experienced this issue?
Update: see [http://ubuntuforums.org/showthread.php?p=2614868#post2614868]("http://ubuntuforums.org/showthread.php?p=2614868#post2614868")

---

