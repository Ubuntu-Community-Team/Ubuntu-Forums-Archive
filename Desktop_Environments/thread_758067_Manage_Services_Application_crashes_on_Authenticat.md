---
title: "Manage Services Application crashes on Authentication"
date: 2008-04-17
forum: Desktop Environments
---

### Post by isrd1 on 2008-04-17
Hello,

When I load the Services Management application accessible from the System=>Administration menu and then click on the 'Unlock' option to alter a service the application reports an authentication failure and hangs completely.  Yet other sudo  and package management tasks, which presumably require authentication succeed.  It isn't only the application that hangs but the whole desktop, the only thing I can do is go to a command shell (Alt+F1) and kill the processes.

Anyone any idea what might be the problem please?

Thanks, Rob

---

### Post by isrd1 on 2008-04-19
Actually it's still doing it, it appears to be the Policy-kit that is locking up, I go into another terminal and kill it and my desktop comes back to life.  Anyway I've switched to Bum (BootUp Manager) and that works fine.  Still curious as to what's causing policy-kit to freeze things though - is it a known problem?

Rob

---

