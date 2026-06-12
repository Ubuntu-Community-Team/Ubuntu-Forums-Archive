---
title: "Ubuntu 18.10 : Problem stanby my laptop"
date: 2018-12-16
forum: Desktop Environments
---

### Post by chris777E on 2018-12-16
Hello,

Since upgrade 18.04 to 18.10 i have one issue with suspend my laptop. He can't go to the standby mode.

Here the log of syslog

```

 systemd[1]: systemd-suspend.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: systemd-suspend.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Suspend.
systemd[1]: Dependency failed for Suspend.
systemd[1]: suspend.target: Job suspend.target/start failed with result 'dependency'.
systemd[1]: sleep.target: Unit not needed anymore. Stopping.

```

Anyone have the same issue and resolve it ?

---

### Post by oldrocker99 on 2018-12-16
What happens when you close the laptop? I've never seen one that didn't suspend when closed.

---

### Post by chris777E on 2018-12-16
No suspend when I close my laptop, He show me login page

---

