---
title: "where the heck is my t-bird mail"
date: 2008-12-18
forum: General Help
---

### Post by kenjjj on 2008-12-18
I am having a problem with the display resolution and in messing with it I set it for a very small resolution to see if the settings would take. They did and the program was almost unusable with the small area shown. There was no way to get it to come back as a larger size by re-booting or anything. I had to delete some icons to get to system bar menu along the top, and then I was able to re-size the resolution, however I could find no way to put the icons back so I simply deleted that user account, but now I cannot find the email from that account. 

Where does thunderbird keep the email, and how can I find it if it is a hidden folder, how do I get 'root access' in the desktop enviorment, I know if I open a terminal I can get that but will it then apply in the desktop environment and let me see otherwise hidden files? 

I cannot see any thunderbird or firefox files anywhere, where are they?

BTW this whole thing with the display resolution really sucks, I really like ubuntu but this comes very close to spoiling it!  I see lots and lots of otehrs are having the same problems...they need a fix fast.
Thanks, -Ken

---

### Post by kanikilu on 2008-12-18
It should be in: /home/[username]/.mozilla-thunderbird/[randomString].default/

If you deleted the user account, hopefully you didn't also remove the directory for the user under /home...

---

### Post by cariboo on 2008-12-18
Your thunderbird files are located in ~/.mozilla-thunderbird. To view hidden files and directories, open Nautilus (Places-->Home Folder) and press Ctrl-h, or click View-->Show Hidden Files.

Jim

---

### Post by kenjjj on 2008-12-19
Thanks all! I found them and was able to get them in text format, not as good as being able to use them with thuderbird, I wonder if I ciopy those into the folder with the other account I bet t-bird would open them, huh? -Ken

---

