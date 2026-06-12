---
title: "Steam doesn't work after upgrade to 13.10"
date: 2013-11-01
forum: Gaming &amp; Leisure
---

### Post by wtleung on 2013-11-01
My Steam client does not work anymore after upgrade from 13.04 to 13.10 (64bit).

A few things happened on same day, 
so I do not know which one was causing the issue.

1. Upgraded from 13.04 to 13.10,
2. Changed to driver nvidia-319, then changing it back to nvidia-current package.
3. Started up Steam, then it showed a dialog doing a steam client upgrade.

I then tried below actions but it still doesn't work,
a. deleted the "/.local/share/Steam/appcache/"
b. re-installed the deb file from "http://store.steampowered.com/"
c. ran command "steam --reset" then it downloaded the update package again but still failed with below messages.


Any help or suggestion is very much appreciated!  Thanks!

Regards,
Raymond

```
[2013-11-02 01:14:53] Download Complete.
[2013-11-02 01:14:53] uninstalled manifest found in /mnt/data/raymond/Steam/package/steam_client_ubuntu12 (1).
[2013-11-02 01:14:53] Found pending update
[2013-11-02 01:14:53] Applying update...
[2013-11-02 01:14:53] Extracting package...
[2013-11-02 01:14:57] Installing update...
[2013-11-02 01:14:58] Cleaning up...
[2013-11-02 01:14:58] Update complete, launching...
[2013-11-02 01:14:58] Shutdown
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /mnt/data/raymond/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[1102/011509:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Steam: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  18 (X_ChangeProperty)
Value in failed request:  0x0
Serial number of failed request:  104
xerror_handler: X failed, continuing
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20131102011508_1.dmp
/mnt/data/raymond/Steam/steam.sh: line 722: 31349 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"


```

---

### Post by mcse2000ca on 2013-11-02
Would try copying the games folder and purging steam deleting the folder and reinstalling and bring you games folder back in.

---

### Post by DoubleW on 2013-11-06
> **mcse2000ca said:**
> Would try copying the games folder and purging steam deleting the folder and reinstalling and bring you games folder back in.

I have the issue too, excact same line (722) and error, sadly enough this doesn't work. Even a completely clean install crashes.

---

### Post by cRaZyBisCuiT on 2013-11-06
Is it a driver issue maybe? Try to make sure your drivers are installed correctly and running.

---

### Post by DanglingPointer on 2013-11-06
Try these steps...
a) First if you are willing, try uninstalling Steam and purge it.  Then reinstall it.  If it still fails try the following steps.

1) Uninstall nvida drivers then purge it. You can use the steps on this link [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely).  Be cautious though and follow the steps in the summary of [NikTh]("http://askubuntu.com/users/95393/nikth")'s post (from that link). 
2) If you have ever had AMD drivers, purge AMD drivers as well from the system.  Sometimes uninstalling leaves config files or crap around which can cause conflict.  This has happened to me.
3) Re-install the Nvidia driver
4) Download glmark2 or Phoronix Test Suite and run a graphics test.  The Unigine tests are the best to confirm the driver is doing what it is supposed to be doing.
5) Assuming point 4 was ok and lets say, you were able to run Unigine Heaven for example; try Steam.  If it fails still then re-do point 'a' above.  This time however you will be reinstalling Steam on top of a fresh driver install.

---

