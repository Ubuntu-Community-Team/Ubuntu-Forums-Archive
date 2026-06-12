---
title: "Steam for Linux not working"
date: 2013-09-13
forum: Gaming &amp; Leisure
---

### Post by mattcayenne on 2013-09-13
Hello, I have installed Steam for Linux on my computer. It worked this morning, but now, when I click on it, it briefly displays an "updating" box, then does not open. I rebooted and typed "steam" into the terminal. It said:
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 2890 with name 0eBlobRegistryMutex_BD01AF3D280B619C71BC66661895203E
removing stale semaphore last operated on by process 2890 with name 0eBlobRegistrySignal_BD01AF3D280B619C71BC66661895203E
removing stale semaphore last operated on by process 2890 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 2890 with name 0eSteamEngineLock
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
[0913/212754:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation

...and it automatically translated : p to :p. I hope that does not mean the terminal is razzing me.
As you can see, I am running ubuntu 13.04 64-bit, my computer is a Zotac Zbox AD03 with an AMD processor. Again, Steam was working *just fine* earlier. Now it is not. I have no idea how to fix it (I'm pretty new to linux of any sort), and help woould be most appreciated. Please, though, don't get too technical.

---

### Post by windy2 on 2013-09-14
This is a known error with Steam which appeared a few hours ago. For more details, please have a look at this thread:

[http://steamcommunity.com/app/221410/discussions/0/864978835653093697/](http://steamcommunity.com/app/221410/discussions/0/864978835653093697/)

For a quick fix, kill steam (or logout and login), open a terminal, and type this command:

```
rm ~/.local/share/Steam/appcache/appinfo.vdf
```

---

### Post by higltypig-e on 2013-09-14
Thankyou windy!!!! :D

---

### Post by Ste_JDM on 2013-09-14
Thanks for the support!

---

