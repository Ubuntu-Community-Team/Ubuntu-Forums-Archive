---
title: "1000's &quot;DriveSeekComplete&quot; msgs during Dapper boot"
date: 2006-06-14
forum: Desktop Environments
---

### Post by jonrkc on 2006-06-14
While booting Dapper the process is slowed tremendously by literally thousands of "DriveSeekComplete error" messages referring to a hard drive that checks out perfectly OK and works OK.  I commented the drive out of /etc/fstab and I still get these messages.  I cannot even interrupt them with CTL+c.  I can physically unplug the drive inside the box, but I'd rather continue using it, as it operates fine, e2fsck shows no problem with it, I can partition it normally.

Any solution aside from physically unplugging?

---

### Post by jonrkc on 2006-06-15
The problem continues though I've disabled all the services I guessed were unnecessary, in /etc/init.d, and examined all the ones called from each runlevel.  

This leads me to think it's a module in the kernel that's somehow calling upon my possibly flakey hard drive.  In which case I'd be out of luck, because kernel compilation is beyond the reach of my skills...  :?

---

