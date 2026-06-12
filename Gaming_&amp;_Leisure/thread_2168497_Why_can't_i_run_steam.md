---
title: "Why can't i run steam???"
date: 2013-08-18
forum: Gaming &amp; Leisure
---

### Post by Hari5g900 on 2013-08-18
Hey guys,
    It's almost frustrating; Steam on linux; I installed it; IT DOESN'T START AFTER UPDATING....
This is what I get if I launch steam through the terminal:
```
ubuntu@ubuntu-linux:~$ steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 8797 with name 0eBlobRegistryMutex_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 8797 with name 0eBlobRegistrySignal_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 8797 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 8797 with name 0eSteamEngineLock
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
[0818/131052:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Steam: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  18 (X_ChangeProperty)
Value in failed request:  0x0
Serial number of failed request:  105
xerror_handler: X failed, continuing
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20130818131048_1.dmp
/home/ubuntu/.local/share/Steam/steam.sh: line 704:  8991 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-58d5d664-4958-4899-b1d8-c73c22130818

```
I don't understand anything written above. Please help me with this.

---

### Post by DarkAmbient on 2013-08-18
Going for a long-shot, what's your locale?

```
locale
```

Also, what is your GPU(s) and what drivers do you use?

```
sudo lshw -c video
```

---

### Post by Hari5g900 on 2013-08-18
Locale:
```
ubuntu@ubuntu-linux:~$ locale
LANG=en_IN.utf8
LANGUAGE=en
LC_CTYPE="en_IN.utf8"
LC_NUMERIC="en_IN.utf8"
LC_TIME="en_IN.utf8"
LC_COLLATE="en_IN.utf8"
LC_MONETARY="en_IN.utf8"
LC_MESSAGES="en_IN.utf8"
LC_PAPER="en_IN.utf8"
LC_NAME="en_IN.utf8"
LC_ADDRESS="en_IN.utf8"
LC_TELEPHONE="en_IN.utf8"
LC_MEASUREMENT="en_IN.utf8"
LC_IDENTIFICATION="en_IN.utf8"
LC_ALL=

```
GPU & Drivers
```
ubuntu@ubuntu-linux:~$ sudo lshw -c video
[sudo] password for ubuntu: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e4300000-e43fffff memory:d0000000-dfffffff ioport:4000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e4400000-e44fffff

```

---

### Post by DarkAmbient on 2013-08-18
Are you able to run glxgears -info?

Have you installed any ppa with intel-drivers?

If not, this might be of value?
[https://wiki.ubuntu.com/Valve#Intel_Graphics](https://wiki.ubuntu.com/Valve#Intel_Graphics)

---

### Post by Hari5g900 on 2013-08-20
Yes, I am able to run glxgears -info
Yes, I did follow those instructions and I have upgraded my system.  Guess I won't be able to play Half Life and Half Life 2 after all :sad:.(Team Fortress,Day of defeat....... Oh God!)

```
ubuntu@ubuntu-linux:~$ steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 8890 with name 0eBlobRegistryMutex_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 8890 with name 0eBlobRegistrySignal_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 8890 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 8890 with name 0eSteamEngineLock
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
[0820/194510:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Steam: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  18 (X_ChangeProperty)
Value in failed request:  0x0
Serial number of failed request:  105
xerror_handler: X failed, continuing
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20130820194507_1.dmp
/home/ubuntu/.local/share/Steam/steam.sh: line 704:  9092 Segmentation  fault      (core dumped) $STEAM_DEBUGGER  "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-a7be7ada-498e-4790-89f7-653ea2130820

```

---

### Post by DarkAmbient on 2013-08-20
What happens if you try

```
steam --reset
```

---

### Post by Hari5g900 on 2013-08-20
Yeah.. and now it is updating all over again

```
ubuntu@ubuntu-linux:~$ steam --reset
Installing bootstrap /home/ubuntu/.local/share/Steam/bootstrap.tar.xz
Reset complete!

```

---

### Post by DarkAmbient on 2013-08-20
So no progress when trying to run steam normally after that then?

---

### Post by wtleung on 2013-10-26
I have been using Steam on Ubuntu for some time, but encountered same error today.
Few things happened today, so I do not know which one is causing the issue.
1. Upgraded from 13.04 to 13.10,
2. Changed to driver nvidia-319, then changing it back to nvidia-current package.
3. Started up Steam, then it showed a dialog doing a steam client upgrade.

> 
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /mnt/data/raymond/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 12266 with name 0eBlobRegistryMutex_F4760DEA8F464E324282A9CA87A094F6
removing stale semaphore last operated on by process 12266 with name 0eBlobRegistrySignal_F4760DEA8F464E324282A9CA87A094F6
removing stale semaphore last operated on by process 12266 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 12266 with name 0eSteamEngineLock
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[1027/023057:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Installing breakpad exception handler for appid(steam)/version(1381282832_client)
Steam: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  18 (X_ChangeProperty)
Value in failed request:  0x0
Serial number of failed request:  104
xerror_handler: X failed, continuing
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20131027023055_1.dmp
/mnt/data/raymond/Steam/steam.sh: line 717: 30733 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes


I already tried 

a. deleted the "/.local/share/Steam/appcache/"
b. re-installed the deb file from "http://store.steampowered.com/"
c. ran command "steam --reset" then it downloaded the update package again but still failed with above messages.

Any more suggestions to help diagnosing the problem?

---

### Post by lukebenes on 2014-01-27
```
Major opcode of failed request: 18 (X_ChangeProperty)

```  is usually caused by a locale issue. See [issue 1420]("https://github.com/ValveSoftware/steam-for-linux/issues/1420")

  You quickly check if this is the problem by running:

  ```
LC_ALL=C steam

```  If this is your problem, set LANG=en_US.UTF-8 in /etc/default/locale

---

### Post by Hari5g900 on 2014-03-20
> **DarkAmbient said:**
> So no progress when trying to run steam normally after that then?
No, the same thing happened all over again

---

