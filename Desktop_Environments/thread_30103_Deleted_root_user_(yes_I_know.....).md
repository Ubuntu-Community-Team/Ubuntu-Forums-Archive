---
title: "Deleted root user (yes I know.....)"
date: 2005-04-27
forum: Desktop Environments
---

### Post by jamiiecb on 2005-04-27
Through a bad script I managed to delete the root account so I can no longer sudo ( I get "root password not found" ). Is there any way to fix this without reinstalling?

Thanks

Jamie

---

### Post by nocturn on 2005-04-27
Yes.

Boot with the livecd, mount your root partition.
Add the root user to /pathtoroot/etc/passwd and if needed to /pathtoroot/etc/group (take the livecd as an example).

unmount and reboot, all should be well again.

---

### Post by jamiiecb on 2005-04-27
Thanks, I thought I would be reinstalling all day.

I can sudo now, but I cant set the root password ( Cannot retrieve authentication service ). Is this ever likely to matte or can I leave it as it is?

Thanks again

Jamie

---

