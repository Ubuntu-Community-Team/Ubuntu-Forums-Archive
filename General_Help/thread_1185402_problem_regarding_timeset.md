---
title: "problem regarding timeset"
date: 2009-06-12
forum: General Help
---

### Post by becoolpal on 2009-06-12
i have set the time in ubuntu but when i use shutdown command in the terminal .it is working with earlier time & not the new time .please help me  i am a beginner to this operating system

---

### Post by lamego on 2009-06-12
Your problem description  is a bit confusion.
Do you manually change the system time but it will revert to a different time after a reboot ?
If I am not mistaken Ubuntu installs the ntpdate utility by default, this means that at every reboot it will synchronize the system time with a remote time server, reverting your manual change.
That time server is accurate, you probably want to correct the timezone to have the proper time offset applied to the system time, not the system time itself which is most likely correct.

---

