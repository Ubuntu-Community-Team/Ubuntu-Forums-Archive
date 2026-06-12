---
title: "A way to automount USB drives without sudo access"
date: 2006-10-04
forum: Desktop Environments
---

### Post by caporaso on 2006-10-04
Can anyone tell me if there is a way to allow USB drives to automount for a user without that user having full sudo access? 

I have a system set up, and several users like to do things like plug in USB drives to print documents or grab music, etc.  The USB drives wouldn't mount until I allowed those users full sudo access, but I'd rather not have that.

Any suggestions?

Thanks!

---

### Post by KingArthur10 on 2006-10-04
Go to your system menu, admin, users and groups.  Double click on the user in question, and go to User Privs.  There at the top should be an option to allow the user to access external storage devices.

---

### Post by caporaso on 2006-10-04
Thanks for the response. I had that enabled, but it still wouldn't let that user mount or unmount external USB drives. Should it have?

---

### Post by KingArthur10 on 2006-10-04
It works fine with all my other machines that I have multiple users enabled on.  My sis-in-law uses her USB drive all the time on one of my machines under her own account.  Another thing to check on each user's account is system/pref/RemovableMedia .  You can set it to automount removable media.

---

