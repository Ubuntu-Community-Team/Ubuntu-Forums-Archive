---
title: "Trash counter is incorrect"
date: 2009-05-08
forum: General Help
---

### Post by mingilicious on 2009-05-08
I'm currently running the new distribution of Ubuntu 9.04. It's going great, but I think I created a problem with my external HD. I think I might have deleted some files off of my HD, but I did not empty the trash before disconnecting my external [USB].

I just realized that since then my trash icon is always full, and when I hover my pointer over it, it says that I have 25 items in Trash. Upon opening the folder, I can find nothing. I've tried to empty it several times, and it doesn't change.

Is there any way that I may reset the counter to zero? I've tried following other posts, nothing has helped me and I cannot find any other posts on this specific issue.

Cheers.

---

### Post by geirha on 2009-05-08
Open the root of the external harddrive in nautilus (the file browser). Then hit Ctrl+h to toggle showing hidden files. Do you see anything like a hidden folder named .trash or .Trash or similar?

---

### Post by mingilicious on 2009-05-08
Yes.

Folder is titled .Trash-1000

folders inside are entitled expunged, files, info

---

### Post by geirha on 2009-05-08
Look in that files folder and see if there are any files you want to keep. If not, just delete the whole .Trash-1000 folder, and the trashcan on the panel should reduce to zero. If you get permission denied, you might need to delete it as the root user. Hit Alt+F2 and run «gksu nautilus» to do that.

Do you have full write access to the drive? I'm guessing maybe you had full write access to the entire drive when you moved those file to the trash, but that you now don't have full write access anymore, thus, you can't clean out the trash there anymore.

---

### Post by mingilicious on 2009-05-08
I was able to delete the folder, but that didn't make a difference in my trashcan. It still says 25 files in Trash... with an empty space.

BTW, thank you for your time, I appreciate any help I can get while learning the ins and outs of this OS.

---

### Post by iitywygms on 2009-05-08
This happened to me recently.  I just removed the trash can from my panel and then added a new one back.  Fixed the issue for me.  Maybe a gnome bug?

---

### Post by mingilicious on 2009-05-08
Thank You.

I tried the method you described, and I also did not find any success.

---

