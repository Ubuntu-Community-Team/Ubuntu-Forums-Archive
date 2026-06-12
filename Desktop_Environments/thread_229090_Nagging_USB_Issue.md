---
title: "Nagging USB Issue"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-08-04
Allow me to vent for a moment. 

Case Study:
I had just completed a very mission critical presentation for some executives from my home computer (ubuntu). I popped in a usb thumb drive, copied over the presentation and cost analysis/benefits assessment, pulled the drive and headed down to Raliegh, NC. 5 hours later I was there and I popped in the thumb drive and to my horror... it was GONE! No presentations, nothing. 

Luckily, I have an FTP server and was able to get the presentations but later the following day I tried several more times and each time Nautilus appears to copy over the files but never actually copies. 

I came to realize that the jump drive was being mounted umask=077. But still, no error msg or anything. 

Question:
How can I make the thumb drive mount as all users write access?

Question:
This is obviously a critical bug. Some sort of access denied message must be displayed to tell the user that the write operation failed. How to submit this bug report?

---

### Post by Thund3rstruck on 2006-08-04
Wow... not a single response. 

Come on guys, surely some of you have usb thumb drives...

---

### Post by asplode on 2006-08-04
Did you right click the drive and click eject before you pulled it out?

---

### Post by Thund3rstruck on 2006-08-04
No, I don't have any icons on my desktop. I've removed them all with the gnome-editor.

---

