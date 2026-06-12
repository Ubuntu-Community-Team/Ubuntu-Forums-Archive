---
title: "Krunner &quot;run as another user&quot;"
date: 2009-11-06
forum: Desktop Environments
---

### Post by drtic113 on 2009-11-06
Hi.
I have problem with KRunner in KDE4. I cannot run GUI application as another user (not root just a different user).
Steps to reproduce: 
Login as usera to KDE then Alt+F2 (starts krunner) + command + click the spanner (it opens the dialog with possibility to "run command as another user" - text may differ because I have another language mutation of Kubuntu). Fill in username: userb and his/her password.  
Then the command to run starts but it runs as usera (instead of userb  I inserted to the dialog). Remark: usera does not have permission to use sudo.
Users of other distros like Debian or SuSE say it works in their systems.
This also worked for me in KDE3 but it is my blocking point in KDE4.

Is there something missing in my installation or do I need to configure something to make it work?
Also some workaround would be fine if the above really does not work. But I need to run GUI application with HW acceleration + sound (so ssh -Y userb@machine is not the righ workaround). I also do not like xhost + workaroud because it is security hole.

---

