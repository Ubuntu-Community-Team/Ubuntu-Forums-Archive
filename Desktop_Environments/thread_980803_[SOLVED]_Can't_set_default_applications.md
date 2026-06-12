---
title: "[SOLVED] Can't set default applications"
date: 2008-11-13
forum: Desktop Environments
---

### Post by PeterVR on 2008-11-13
I don't want to open .wmv files in the default video player (Totem), but in MPlayer. 
So I select a .wmv file, click the "Open With" tab in the Properties and select the "MPlayer Movieplayer" line.
This results in an error window:
"Could not set as default application" -
"Could not set application as the default: Failed to create file '/home/peter/.local/share/applications/mimeapps.list.EFWCKU': Permission denied"

I tried this with sudo, but as expected I only manage to change the root prefs this way.

Now what?

---

### Post by mcduck on 2008-11-13
Based on the error message something (like running GUI apps with "sudo" instead of "gksudo"..) has caused the permissions of the directory to change from the defaults, leaving you without write permission to that directory.

So, check the directory's ownership & permissions, it should belong to you and you should have read/write access there.

---

### Post by PeterVR on 2008-11-13
Yeah, it was that simple.
 sudo chown peter applications 
did the trick.

Thanks

---

### Post by asn_knight on 2010-08-20
Can you explain how you did it? 
I got the exact same error.
How do you change those settings from the terminal?
Thanks.

---

### Post by asn_knight on 2010-08-22
Hey! 
I used the instructions of using 'chown' from
[http://ubuntuforums.org/showthread.php?t=479841](http://ubuntuforums.org/showthread.php?t=479841)

It gave me some error when I executed but sure solved the job..! :)
No probs after tht! :)

---

