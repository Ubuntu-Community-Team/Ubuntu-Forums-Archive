---
title: "Trash icon, not emty, when empty"
date: 2013-09-26
forum: Desktop Environments
---

### Post by Azyx on 2013-09-26
The problem is that when I empty the trash, the 'trash-icon' are still full, booth in the Laucher and that one on the desktop.

Using Ubuntu 12.04LTS and tthe problems appears on both machine I use, but it work some-times.

/Cheers

---

### Post by slickymaster on 2013-09-26
Try this:```
rm -rf ~/.local/share/Trash/files
```

---

### Post by Azyx on 2013-09-26
Hi slickymaster. I did not work.

---

### Post by slickymaster on 2013-09-26
Did any of the items trashed come from any sort of a external storage device (USB, etc.)? If that's the situation one thing you can do is to empty the trash with that drive mounted.

There's an already reported LP bug: [Bug #1076121]("https://bugs.launchpad.net/unity/+bug/1076121"). If you are experiencing the same behavior, you can click on the green line "This bug affects ? users. Does it affect you?" -> "Yes, it affects me too."

---

### Post by Azyx on 2013-09-26
Thanx. I have reported.

---

### Post by slickymaster on 2013-09-26
I'm assuming that you were facing the same problem. Did you manage to solve it? If yes, please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Azyx on 2013-09-26
No. I did not solved it, but consider it as a feature ;)

---

