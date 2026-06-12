---
title: "google-drive-ocamlfuse and multiple users"
date: 2023-01-06
forum: Desktop Environments
---

### Post by zeke2135 on 2023-01-06
I'm kind of behind the curve but I just discovered google-drive-ocamlfuse. It works great to help w/ using luckybackup (based on rsync) to back up my personal data to my google drive. However, I'd like to back up my kids' data as well. But the mounted google drive doesn't seem to be available outside my login. I assume because it basically doesn't exist outside of my session. For example even sudo ls gives me a permission denied. So I don't have permission to access the files in my kids' home directories from my login, and I can't see the destination drive if I attempt root access. 

I hope the above is reasonably clear. I'd like to know if I'm missing a straightforward way to do what I described. I'm using ubuntu 22.04.1 BTW I am using rsync at present to back up to a local drive.
thanks

---

