---
title: "Controlling startup services and applications"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Zunino on 2006-09-23
Hello.

In Windows, one usually has three places to look for when wishing to know what applications or services are being automatically run when the system starts, namely: 1) the 'Run' key in the system registry; 2) the 'Startup' shortcuts menu and 3) the services control panel.

In Ubuntu, I already found the "Services settings" control panel, available under System > Administration. It allowed me, for instance, to keep mysqld and apache2 from starting up automatically. However, the items displayed in that list do not match the full list of applications/services that are actually loaded at startup (e.g. when I shutdown Ubuntu, I can see a BitTorrent tracker service being shut down).

So, the basic question is: in Ubuntu (or Linux in general), what are the main places one should look into in order to find out and control which services should be automatically loaded?

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by henriquemaia on 2006-09-23
If you're not afraid of using the terminal, you can install **sysvconfig **(available on the repositories) and then, after the installation is complete, invoke it on the terminal running:

```
sudo sysvconfig
```

You can then edit all services available during boot.

---

