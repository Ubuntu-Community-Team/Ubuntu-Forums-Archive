---
title: "Steam Completely Crashing on Startup (12.04)"
date: 2013-12-11
forum: Gaming &amp; Leisure
---

### Post by james.bianchi on 2013-12-11
Hey all, 

I am having a problem running steam on my dedicated server that is running Ubuntu 12.04
I have installed steam fine and when I go to run it, the "Updating steam" window pops up for a quick second and then steam apparently crashes.
The computer has the intel integrated graphics controller.

When I run in the terminal I come up with this error:

```
Running Steam on ubuntu 12.04 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1386125885_client)
Installing breakpad exception handler for appid(steam)/version(1386125885_client)
Installing breakpad exception handler for appid(steam)/version(1386125885_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 395 with name 0eBlobRegistryMutex_076F896E8DFB79E50480B1A7BC3BE862
removing stale semaphore last operated on by process 395 with name 0eBlobRegistrySignal_076F896E8DFB79E50480B1A7BC3BE862
removing stale semaphore last operated on by process 395 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 395 with name 0eSteamEngineLock
OpenGL GLX extension not supported by displayAssert( Assertion Failed: Fatal Error: OpenGL GLX extension not supported by display ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/Main.cpp:284


Installing breakpad exception handler for appid(steam)/version(1386125885_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20131211124129_5.dmp
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-0127305a-bafe-4cb9-af65-a96262131211

```

Any help would be greatly appreciated. I have tried anything and even tried to run it on PlayonLinux and am still running into the same crashing problem.

Thank you
Jimmy

---

