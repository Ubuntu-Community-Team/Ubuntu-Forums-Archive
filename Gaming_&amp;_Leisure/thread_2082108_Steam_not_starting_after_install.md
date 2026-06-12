---
title: "Steam not starting after install"
date: 2012-11-07
forum: Gaming &amp; Leisure
---

### Post by DesertTurtle on 2012-11-07
I installed from the .deb, but whenever I try and run Steam from the terminal or quicklist it says that it cannot connect to the network. It works fine on Windows and WINE...

Here's the string I get in a terminal:

```
steam steam://open/games
Installing breakpad exception handler for appid(steam)/version(1352224866_client)
unlinked 0 orphaned pipes
[1107/125344:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835.58 KB
```

I'm running Ubuntu 12.04 64-bit.

Any ideas?

---

### Post by snafu006 on 2012-11-07
> **DesertTurtle said:**
> I installed from the .deb, but whenever I try and run Steam from the terminal or quicklist it says that it cannot connect to the network. It works fine on Windows and WINE...

Here's the string I get in a terminal:

```
steam steam://open/games
Installing breakpad exception handler for appid(steam)/version(1352224866_client)
unlinked 0 orphaned pipes
[1107/125344:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835.58 KB
```I'm running Ubuntu 12.04 64-bit.

Any ideas?

you need the 32 bit libs,  sudo apt-get install ia32-libs

---

### Post by kchaosrei on 2012-11-08
> **DesertTurtle said:**
> I installed from the .deb, but whenever I try and run Steam from the terminal or quicklist it says that it cannot connect to the network. It works fine on Windows and WINE...


Any ideas?


I am having the same issue on the 32 bit. any ideas from anyone?

---

### Post by sffvba[e0rt on 2012-11-08
**Posts moved to a support thread... (lets leave the other threads for solutions once we have found it here)...**

As for the terminal output, it doesn't contain an error pointing to the issue.  The last few lines shows that it should be displaying a dialogue box showing that Steam is attempting to connect to the server...

What you can check out is ~/Steam/steam.log and see if there are any error messages and post them here (if in doubt post the whole log).

BTW, what graphics are you running (I have heard of people that updated their drivers to the latest and it fixed some issues for them).


404

---

### Post by miquelb on 2012-11-13
Hello everyone,
I have got the same problem. I installed the steam client. Afterwards, it updated. Then a login window comes out but when attempting to login I have this error message
I am using ubuntu 12.04 64-bits. Thanks in advance

---

### Post by Hari5g900 on 2013-08-02
```
ubuntu@ubuntu-linux:~$ steamRunning Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 9324 with name 0eBlobRegistryMutex_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 9324 with name 0eBlobRegistrySignal_01ADCAAE08B43E5E8AE44675F4157195
removing stale semaphore last operated on by process 9324 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 9324 with name 0eSteamEngineLock
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
[0802/205232:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
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
/tmp/dumps/crash_20130802205228_1.dmp
/home/ubuntu/.local/share/Steam/steam.sh: line 704:  9569 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-b19788d9-4a4d-47a2-a881-9e6b32130802

```

I can't start steam after instaling and updating, any ideas?

---

### Post by oldrocker99 on 2013-08-02
A segmentation fault is ** usually ** due to a graphics driver problem; what is your video card and which drivers are installed?

---

### Post by Hari5g900 on 2013-08-02
I don't know about the driver but I have an Intel GMA X3100(I know, I know, I'll have to put in a new one soon)

---

### Post by oldrocker99 on 2013-08-02
OK, you **might** try this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

Steam works better with the drivers (including Intel drivers) from this PPA. In fact, they recommend it.

---

### Post by Hari5g900 on 2013-08-07
> **oldrocker99 said:**
> OK, you **might** try this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

Steam works better with the drivers (including Intel drivers) from this PPA. In fact, they recommend it.

Well, that didn't work. I also opened up additional drivers and it said that I had NO proprietary drivers installed. So does that mean I have to install something?

---

### Post by oldrocker99 on 2013-08-07
The open-source Linux drivers for Intel are better than you might expect, from my experience with a Sandy Bridge Chromebook. There aren't any proprietary Linux Intel drivers, in fact; Intel works pretty closely with the open source developers, and posts source code for all their drivers. Open Synaptic and do a search (not a quick search) for intel; you may see files that aren't installed, or files with an up arrow on them, meaning that they're upgradeable.

And good luck.

---

### Post by Hari5g900 on 2013-08-08
> **oldrocker99 said:**
> The open-source Linux drivers for Intel are better than you might expect, from my experience with a Sandy Bridge Chromebook. There aren't any proprietary Linux Intel drivers, in fact; Intel works pretty closely with the open source developers, and posts source code for all their drivers. Open Synaptic and do a search (not a quick search) for intel; you may see files that aren't installed, or files with an up arrow on them, meaning that they're upgradeable.

And good luck.

X.Org X server -- Intel i8xx, i9xx display driver
This and some 4 other X.Org programs were not installed. But when I marked it for installation, a lot of other software was to be removed including Ubuntu-desktop. I'm not sure I'm supposed to install this or not.

---

### Post by oldrocker99 on 2013-08-08
Go ahead and install, making note of which programs are to be removed, then install and resinstall the removed programs; ubuntu-desktop removal will not break your system.

---

### Post by Hari5g900 on 2013-08-08
> **oldrocker99 said:**
> Go ahead and install, making note of which programs are to be removed, then install and resinstall the removed programs; ubuntu-desktop removal will not break your system.

I forgot to mention earlier, the package also says-'it's quantal', 'it's raring' etc. I can't find 'it's precise' though.

---

