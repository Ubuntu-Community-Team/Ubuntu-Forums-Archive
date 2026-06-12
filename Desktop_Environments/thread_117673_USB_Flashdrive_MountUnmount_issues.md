---
title: "USB Flashdrive Mount/Unmount issues"
date: 2006-01-15
forum: Desktop Environments
---

### Post by cajunaggie on 2006-01-15
I have a 1GB Attache USB flashdrive. It worked great the first couple of times I used it. However now I'm running into some issues.
For example, sometimes when I delete a file from the drive the window shows the file as gone, but after I take it out and plug it back in, the file is there in all it's glory. Othertimes Ubuntu refuses to unmount the flashdrive and any attempt to mess with the drive gives me an error message saying I don't have permissions. 
Is this a common bug or am I missing a driver somewheres? :confused:

---

### Post by AAUU on 2006-01-15
The drive automounts or you're mounting it manually?

Do you umount the drive after you delete the files, or do you just pull it out?  (umount could be the umount command or the right click on the drive located on the desktop and select "unmount volume" or something similar)

---

### Post by cajunaggie on 2006-01-15
It automounts and autounmounts. I've tried just pulling it out and tried manually unmounting it. Same results

---

### Post by NoNo_231 on 2006-01-15
I had the same problem but I found that unmounting the drive manually solves the problem.

---

### Post by AAUU on 2006-01-15
Yeah, I was going to say that umount'ing before you pull the drive usually fixes that issue.  If you delete a file on the USB, then umount it, then pull it I'd be surprised if the file is still on the USB device.

[EDIT]
Also, if you've got a shell open and you're in a directory within the USB device it will tell you it's busy if you try to umount it.

---

