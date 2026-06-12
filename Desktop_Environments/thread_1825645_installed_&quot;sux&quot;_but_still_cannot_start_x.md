---
title: "installed &quot;sux&quot; but still cannot start x app remotely"
date: 2011-08-15
forum: Desktop Environments
---

### Post by Pollywoggy on 2011-08-15
I installed sux and then tried again to start a KDE app after connecting to the other user's account using the sux command:

sux - user5

When I try to start the KDE app I get this:

kate: cannot connect to X server :0.0

Both users are on the localhost and I will have to set up SSH on the other user if I can't get sux to work.

Any ideas why sux is not facilitating this app to run in another user's session?

---

### Post by Toz on 2011-08-15
You need to explicitly allow access to the X server. This works for me:
```

xhost +
su - user
kate
```

For more information: ```
man xhost
```

---

