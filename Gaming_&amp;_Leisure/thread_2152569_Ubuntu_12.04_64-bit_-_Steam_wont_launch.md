---
title: "Ubuntu 12.04 64-bit - Steam wont launch"
date: 2013-06-08
forum: Gaming &amp; Leisure
---

### Post by rgallagher892 on 2013-06-08
Hi all, was wondering if anyone could help me sort out my woes.

Have been trying to install Steam in Ubuntu 12.04LTS all morning and am having no luck. When I try to launch it, nothing happens. Launching it from the terminal gives:

rob@rob-VPCSE2C5E:~$ steam
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 2709 with name 0eBlobRegistryMutex_CA4827D333CB3458EBB49EB922A05FDE
removing stale semaphore last operated on by process 2709 with name 0eBlobRegistrySignal_CA4827D333CB3458EBB49EB922A05FDE
removing stale semaphore last operated on by process 2709 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 2709 with name 0eSteamEngineLock
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  34
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  63
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
Serial number of failed request:  92
xerror_handler: X failed, continuing
glXChooseVisual failedrob@rob-VPCSE2C5E:~$ ^C

I am fairly new to Ubuntu, and have had 13.04 for a few months, but have had problems with it so downgraded to the LTS edition available. I have all updates installed, and have the ATI/AMD proprietary FGLRX graphics driver (**experimantal** beta) installed. My lapton has the following specs:

Intel i5-2450M 2.50GHz
500GB Sata 5400rpm
AMD Radeon HD 6630M 1GB dedicated
8GB 1333mHz DDR3-SDRAM

so it has the power to run it all. As I said I am running 12.04LTS and any help would be appreciated. Thanks

---

### Post by CatKiller on 2013-06-08
Do you have the same problem if you aren't running beta drivers?

---

### Post by rgallagher892 on 2013-06-08
> **CatKiller said:**
> Do you have the same problem if you aren't running beta drivers?

I have that problem regardless of which driver I am using, trying installing catalyst now

---

### Post by CatKiller on 2013-06-08
This bit
```
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
```

looks like a graphics problem of some kind. I have no experience of using Ati graphics under Linux, though.

---

