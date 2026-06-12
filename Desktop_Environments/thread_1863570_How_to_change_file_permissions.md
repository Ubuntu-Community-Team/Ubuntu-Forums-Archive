---
title: "How to change file permissions???"
date: 2011-10-17
forum: Desktop Environments
---

### Post by HonorFace on 2011-10-17
I'm trying to access and edit some Robocode sample robots so I can learn how to play the game and advance my Java skills, etc. 

BUT

nothing seems to change the file permissions on them. I tried 
sudo chmod ugo+rwx robotsfile
as a last resort, and STILL nothing.

How can I unlock these files???

---

### Post by meatytaco on 2011-10-18
Try
```
sudo chmod 777 <filename>
```
That grants everyone to do everything to that file.
As always, gotta be careful changing permissions if the file is important. (In your case, you seem good) :P

---

### Post by mcduck on 2011-10-18
> **HonorFace said:**
> I'm trying to access and edit some Robocode sample robots so I can learn how to play the game and advance my Java skills, etc. 

BUT

nothing seems to change the file permissions on them. I tried 
sudo chmod ugo+rwx robotsfile
as a last resort, and STILL nothing.

How can I unlock these files???

Did you get any errors? How are you trying to launch the game? And most importantly, where are the files located? You can't change permissions of files located on Windows file systems, as those filesystems lack the support for Posix permissions.

(And finally, you don't really even need to make any Java files executable, as you don't actually execute them like you would a native binary application or a script. You are simply opening them with Java. Just like you don't need to make a .jpg image executable because you open it with an image viewing program. You only need to make them executable if you want to execute them by double-clicking, as opposed to starting them with a launcher, some script, a command in terminal or simply by choosing to open the file with Java.)

---

