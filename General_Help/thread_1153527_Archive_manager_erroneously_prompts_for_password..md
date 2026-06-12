---
title: "Archive manager erroneously prompts for password."
date: 2009-05-08
forum: General Help
---

### Post by jeremyjjbrown on 2009-05-08
I'm having a problem that and I'm not seeing other posts on it.

Archive manager on my 8.04 laptop and desktop is erroneously asking for a  password during unrar of archives. If I scan these files with PAR2 no errors are reported. If I move the files to my xp machine winrar unpacks these .rar archives without issue. I did not have this problem when 8.10 was installed. I'd rather not move the very large files to a different machine just to unoack them, and I prefer to stay with LTS on my main computer.

Thanks.

---

### Post by sgosnell on 2009-05-08
Are you sure it isn't just asking for an admin password to allow extracting the files to a folder owned by root?

---

### Post by jeremyjjbrown on 2009-05-08
Upon further searching this has been a problem since 7.10. Maybe since unrar is on 3.8 Ubuntu could update the repository version up from 1.3 so we can have a version that isn't five years old.:confused:

It's either use wine for winrar (platinum rating) or compile rar from source. Since I'm a noob at compiling and have yet to find an noobs guide to compiling it is Wine for now.

---

### Post by jeremyjjbrown on 2009-05-08
> **sgosnell said:**
> Are you sure it isn't just asking for an admin password to allow extracting the files to a folder owned by root?

That was a good idea that I hadn't tried unfortunatley not the problem.

Thanks

---

### Post by sgosnell on 2009-05-08
Ummm... the version in the repositories is 3.8.5-1.  The 1: in front isn't the version number.

---

### Post by NFblaze on 2009-05-08
> **jeremyjjbrown said:**
> That was a good idea that I hadn't tried unfortunatley not the problem.

Thanks

Try Peazip.

---

