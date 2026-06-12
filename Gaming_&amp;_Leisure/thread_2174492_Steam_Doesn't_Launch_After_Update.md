---
title: "Steam Doesn't Launch After Update"
date: 2013-09-14
forum: Gaming &amp; Leisure
---

### Post by jacob9 on 2013-09-14
So after I closed my Steam to allow it to update, I thought it'd was smooth.. But when I tried to open it, it just says "Veryifying Installation" and then closes... I've restarted my computer, updated Linux to the latest Kernel, updated my Nvidia drivers to 325.08, did a complete refresh install of Steam, and I've created new sessions.. Then I thought it'd be a good idea to see the errors from terminal... Welp, here they are.

soarin@soarin-GA-78LMT-S2P:~$ steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 4518 with name 0eBlobRegistryMutex_A911CEC87A88E67E7463ECCD20D44EFF
removing stale semaphore last operated on by process 4518 with name 0eBlobRegistrySignal_A911CEC87A88E67E7463ECCD20D44EFF
removing stale semaphore last operated on by process 4518 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 4518 with name 0eSteamEngineLock
Installing breakpad exception handler for appid(steam)/version(1378500910_client)
[0914/170631:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation



Help? :( 

*Note
It all worked before, I was playing Garry's Mod for about a week or three.

---

### Post by jacob9 on 2013-09-14
I FOUND A FIX, FROM GTUX ON STEAM FORUMS!


[fix]
killall steam
rm -Rf ~/.steam/steam/appcache
steam

---

### Post by Deleted20200712 on 2013-09-14
Thank you, had the same problem, and your fix worked!

---

### Post by TheCadaver on 2013-09-15
Thanks! I had a similar but different problem, but it worked for me too.

---

### Post by daaxwizeman on 2013-09-19
Cool, it works for me.

But why is this happening ?

---

