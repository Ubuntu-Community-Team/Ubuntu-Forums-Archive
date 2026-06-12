---
title: "Change location of .ICEauthority file"
date: 2010-07-09
forum: Desktop Environments
---

### Post by disik on 2010-07-09
Hello,
I need to change the location where xmanager in Ubuntu 10.04 expects to find a .ICEauthority file. How can I do that? Don't ask me why.

---

### Post by Yarui on 2010-07-09
I'm not quite sure what exactly you are going for.  Maybe if we knew more about what you were attempting to do we would be able to come up with some suggestions.

---

### Post by disik on 2010-07-09
Okay,
I set up Ubuntu 10.04 into a Oracle Vortualbox. I plan to have a virtual disk with a ready virtual machine same for all users, being overwrited each week with an updated one.
I want users have their home directories on their host machines, I do this by mounting a virtualbox shared folder (vboxsf).
When a user tries to log in something (an xmanager?) wants to lock the file /home/username/.ICEauthority. It happens okay when this file stays on a filesystem that supports locking, but vboxsf filesystem seems not to support that so I gen an annoying error message 'Could not update ICEauthority /home/usrname/.ICEauthority file'
So I want to get rid of this message by placing .ICEauthority somewhere into /var/username directory.
How can I do that?

---

### Post by disik on 2010-07-12
Or please advise me where to ask.

---

