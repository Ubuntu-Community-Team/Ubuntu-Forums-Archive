---
title: "quick way to move file and create symbolic link"
date: 2009-06-08
forum: General Help
---

### Post by GrimRe on 2009-06-08
Hi

I'm trying to achieve the following using some kind of script or just cli commands.

[LIST=1]
[*]Move directory to new location
[*]Create symbolic link in place of moved directory
[/LIST]

This can be achieved through:

```
mv old/location/dir1 /new/location/
ln -s /new/location/dir1 /old/location/dir1

```

But is there anyway I can automate the process into 1 command so I can run it from say cron?

Does this make sense?

Thanks.

---

### Post by nikhilk on 2009-06-08
> **GrimRe said:**
> 
But is there anyway I can automate the process into 1 command so I can run it from say cron?


If your ultimate goal is to run the action via cron, you can add the commands in a bash script file and then run that file via cron.
Just be sure to use absolute paths even for mv and ln commands as the same environment, that you normally have, might not be set for cron jobs.

---

