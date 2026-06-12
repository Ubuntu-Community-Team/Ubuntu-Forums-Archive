---
title: "&quot;The specified location is no longer mounted&quot; occurs an hour of transfering data"
date: 2010-10-14
forum: Desktop Environments
---

### Post by CorvetteFan86 on 2010-10-14
Hello all,

I am using Ubuntu Desktop Edition version 10.04. I have it setup as a file share (Samba). I am in the process of moving my data from my backup on my other desktop to this one. The share on the windows 7 box is everyone allowed. When I start transferring data (80-100gb) to the samba share about 3/4 of the way through it the linux box will give me an error message saying the "The specified location is no longer mounted". I can then remount it just fine but the same thing occurs again. Is there a setting in my smb.conf that I need to add/enable? Any help would be appreciated.

NOTE - The share on the Ubuntu Desktop is password protected.

Thanks,
Thomas

---

### Post by CorvetteFan86 on 2010-11-17
So a figured out a "Workaround" for this issue. If I navigate to **Places** > **Network** then navigate to the share I want to connect to I authenticate by putting in my password and the "mapped drive" stays connected. Just in case someone else has the same issue!

---

