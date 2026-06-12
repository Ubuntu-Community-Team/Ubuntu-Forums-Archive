---
title: "Steam"
date: 2013-04-14
forum: Gaming &amp; Leisure
---

### Post by 3dmatrix on 2013-04-14
I installed Steam from the Ubuntu Software center and I have the steam icon on my desktop but i get the following errors

**Updating Steam . . . . Checking for available updates**
It downloads just a few Kb every time and then displays an Error :
**Fatal Error : Steam needs to be online to update. Please confirm your network connection and try again.**
(though my internet was working fine)
After trying multiple times, i got another error :
**You are missing the following 32-bit libraries, and steam may not run : libc.so.6**
On checking in synaptic i found it was related to Clam AV and it wanted to install a lot of packages along with it.
Why do i need to do that ? And any way will it help if i install all that ? Why the network error ?

Can any one advise ?

---

### Post by myromance123 on 2013-04-15
Does your system have a 32Bit Ubuntu install, or a 64Bit Ubuntu install?

Have you tried doing this first, to resolve the 32-bit libraries dependency?
```
sudo apt-get install ia32-libs
```

---

### Post by soloman469 on 2013-04-16
Are you sure that the speed of your internet is optimal? (what i mean is how many MBps do you get, or what is your internet speed.)

---

### Post by 3dmatrix on 2013-04-16
> **soloman469 said:**
> Are you sure that the speed of your internet is optimal? (what i mean is how many MBps do you get, or what is your internet speed.)

My internet speed is perfectly fine. There is some other prob.

---

### Post by 3dmatrix on 2013-04-16
> **myromance123 said:**
> Does your system have a 32Bit Ubuntu install, or a 64Bit Ubuntu install?

Have you tried doing this first, to resolve the 32-bit libraries dependency?
```
sudo apt-get install ia32-libs
```

I tried to install it but it was not found. So i checked up in synaptic and it showed somthing like, ia32-libs-multivers
I installed but still steam was giving errors.
The next day i tried again and this time steam started upgrading itself and downloaded some 150+Mb. But while installing it said there was not enough space on the HDD so i had to make some space and continue but seems the installation was not ok. Anyway, I reached the next stage where Steam asked me to register and here it stays forever saying the password is weak. Even if i use very complicated password it still remains there and after some time it displays an error that it is not able to connect to the server.

What is going wrong ? No other software is facing any internet issue.

---

### Post by soloman469 on 2013-04-16
How old is your computer? How much RAM do you have in it? Processor speed?

---

### Post by myromance123 on 2013-04-17
This is very strange. Can you please run Steam via Terminal, and post the output here?
If you can, please also highlight any ERRORs it gives.

To run Steam via Terminal, just enter this into any Terminal and hit Enter:
```
steam
```

---

### Post by 3dmatrix on 2013-04-17
> **soloman469 said:**
> How old is your computer? How much RAM do you have in it? Processor speed?


Ubuntu 12.04 32-bit
Gnome 3.4.2

CPU : Intel 2.1 x 2
RAM : 2Gb

Its not a prob with the computer or internet.
Everything else works fine including other online games.

---

### Post by soloman469 on 2013-04-17
I think you should get more RAM, just a suggestion...

---

### Post by Bölvaður on 2013-04-17
> **soloman469 said:**
> I think you should get more RAM, just a suggestion...

Just to clarify, 2 GiB of RAM is sufficient to run Steam, and more RAM is not needed for most games available on Steam.


The problem is that you need the ia32-libs package. It's a library that contains everything you need to run 32 bit software on 64 bit Linux OS.
The reason why you are having those problems can occur because of multiple possibilities.

How did you install Steam and where from did you get it?
Can you please do as requested above and post the terminal output when running Steam from the terminal.

---

### Post by 3dmatrix on 2013-04-17
steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
unlinked 0 orphaned pipes
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
[0417/220311:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835.58 KB
Generating new string page texture 18: 64x256, total string texture memory is 901.12 KB
Generating new string page texture 21: 8x256, total string texture memory is 909.31 KB
Generating new string page texture 22: 16x256, total string texture memory is 925.70 KB
Generating new string page texture 23: 32x256, total string texture memory is 958.46 KB
Generating new string page texture 24: 24x256, total string texture memory is 983.04 KB
Process 2896 created /user-ValveIPCSharedObjects3
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Generating new string page texture 37: 1024x256, total string texture memory is 2.03 MB
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 1259 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 2 multi object alertable sleeps
[2013-04-17 22:03:01] Startup - updater built Mar 29 2013 11:40:39
[2013-04-17 22:03:02] Verifying installation...
[2013-04-17 22:03:02] Verification complete
Shutting down. . .
[2013-04-17 22:05:01] Shutdown

As usual i kept waiting for long time and finally canceled the operation.

---

### Post by 3dmatrix on 2013-04-17
> **Bölvaður said:**
> Just to clarify, 2 GiB of RAM is sufficient to run Steam, and more RAM is not needed for most games available on Steam.


The problem is that you need the ia32-libs package. It's a library that contains everything you need to run 32 bit software on 64 bit Linux OS.
The reason why you are having those problems can occur because of multiple possibilities.

How did you install Steam and where from did you get it?
Can you please do as requested above and post the terminal output when running Steam from the terminal.

I know RAM is not the problem. Just a reminder, I am using 32 bit Ubuntu.

---

### Post by 3dmatrix on 2013-04-19
Can any one help ?

---

### Post by myromance123 on 2013-04-19
Your problem is very peculiar. Since you're on a 32Bit version of Ubuntu, you shouldn't have any problems with 32Bit dependencies.

My only guess is that the version of Steam you obtained from the Ubuntu Software Center is corrupted/broken, or could have become broken during installation. Have you tried getting the .deb installer from Steam's website?
Get it here: [http://store.steampowered.com/about/?snr=1_4_4__11]("http://store.steampowered.com/about/?snr=1_4_4__11")

Before trying to install this, please uninstall/remove the Steam you installed from the Ubuntu Software Center. To install the .deb from Steam's website, simply download it and double click it. It will then proceed to use the USC to install itself. I find this is usually the safest way to go about it.

---

### Post by 3dmatrix on 2013-04-20
> **myromance123 said:**
> Your problem is very peculiar. Since you're on a 32Bit version of Ubuntu, you shouldn't have any problems with 32Bit dependencies.

My only guess is that the version of Steam you obtained from the Ubuntu Software Center is corrupted/broken, or could have become broken during installation. Have you tried getting the .deb installer from Steam's website?
Get it here: [http://store.steampowered.com/about/?snr=1_4_4__11]("http://store.steampowered.com/about/?snr=1_4_4__11")

Before trying to install this, please uninstall/remove the Steam you installed from the Ubuntu Software Center. To install the .deb from Steam's website, simply download it and double click it. It will then proceed to use the USC to install itself. I find this is usually the safest way to go about it.

I uninstalled it but it seems it is not completely uninstalling as after installing from the downloaded deb it is not downloading the new installation files of abt 150+ mb. it is straight off going to the next stage for login. So how can i make sure that all the files it earlier downloaded are uninstalled or deleted ?

---

### Post by myromance123 on 2013-04-20
Following this: [LINK]("http://askubuntu.com/a/217875/60536")

Open a new terminal and Enter each of the following one-by-one.
```
sudo apt-get remove steam
```
```
sudo apt-get purge steam
```
```
rm -rf ~/.local/share/Steam
```

Now, try and reinstall Steam.

The last instruction is the most important. This one goes to your hidden Steam folder and deletes it. You can check if it's deleted later by going into your Home directory, clicking View -> Show Hidden Files and then heading into .local/share/Steam.

---

### Post by 3dmatrix on 2013-04-20
> **myromance123 said:**
> Following this: [LINK]("http://askubuntu.com/a/217875/60536")

Open a new terminal and Enter each of the following one-by-one.
```
sudo apt-get remove steam
```
```
sudo apt-get purge steam
```
```
rm -rf ~/.local/share/Steam
```

Now, try and reinstall Steam.

The last instruction is the most important. This one goes to your hidden Steam folder and deletes it. You can check if it's deleted later by going into your Home directory, clicking View -> Show Hidden Files and then heading into .local/share/Steam.

I did every thing as instructed.
First when i wanted to remove steam it said it is not installed and use auto remove for unwanted applications. I did that and it removed a lot of applications.
Then i followed the rest as you instructed and finally steam downloaded abt 150+ mb of data (though once there was a network error but i tried again and it worked). But finally even after the entire installation was done it gave the same network error (can not connect to the server). I registered on steam's website instead of from that software and this time clicked login with existing id but it again gave the same network error where as there is no problem with internet usage. The terminal response is :

**steam**
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
unlinked 0 orphaned pipes
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
[0421/012638:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835.58 KB
Generating new string page texture 18: 24x256, total string texture memory is 860.16 KB
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 276 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 1 multi object alertable sleeps
[2013-04-21 01:26:34] Startup - updater built Mar 29 2013 11:40:39
[2013-04-21 01:26:34] Verifying installation...
[2013-04-21 01:26:34] Verification complete
Shutting down. . .
[2013-04-21 01:26:59] Shutdown

---

### Post by myromance123 on 2013-04-20
This is starting to look like an issue with Steam itself rather than your system. Alright, can you uninstall it all the same as before but this time with one difference. In your Home folder, click View -> Show Hidden Files. There's one more folder that might exist containing Steam files. This is the .steam folder. If after you've uninstalled Steam, this folder still exists than we can assume this folder may be the problem. Please delete it as well (after doing the uninstall commands as instructed above). Now try once more with reinstalling Steam. (Note, the .steam folder is NOT the same one as the /.local/share/Steam folder)

If it still fails after this, I can only guide you to publish this as an issue on Steam's Github issues page: [https://github.com/ValveSoftware/steam-for-linux/issues]("https://github.com/ValveSoftware/steam-for-linux/issues")
You will need a free Github account to post your issue, but hopefully the folks there can further assist you. To publish an issue, just click the big green New Issue button on the top right of the page.

P.S: Could it also be possible that your Ubuntu installation might be corrupted? This can happen when upgrading and/or doing a clean install with a CD or USB. I have personally experienced corrupt installs with Ubuntu and Windows, it's natural.

---

### Post by 3dmatrix on 2013-04-20
> **myromance123 said:**
> This is starting to look like an issue with Steam itself rather than your system. Alright, can you uninstall it all the same as before but this time with one difference. In your Home folder, click View -> Show Hidden Files. There's one more folder that might exist containing Steam files. This is the .steam folder. If after you've uninstalled Steam, this folder still exists than we can assume this folder may be the problem. Please delete it as well (after doing the uninstall commands as instructed above). Now try once more with reinstalling Steam. (Note, the .steam folder is NOT the same one as the /.local/share/Steam folder)

If it still fails after this, I can only guide you to publish this as an issue on Steam's Github issues page: [https://github.com/ValveSoftware/steam-for-linux/issues]("https://github.com/ValveSoftware/steam-for-linux/issues")
You will need a free Github account to post your issue, but hopefully the folks there can further assist you. To publish an issue, just click the big green New Issue button on the top right of the page.

P.S: Could it also be possible that your Ubuntu installation might be corrupted? This can happen when upgrading and/or doing a clean install with a CD or USB. I have personally experienced corrupt installs with Ubuntu and Windows, it's natural.

Thanx, I will check these things one by one. But i will not be able to reply for two days. Anyway, if (in case) there is prob with Ubuntu then how do we check that ? I do not wish to reinstall Ubuntu again, its a big trouble updating and installing everything. And i have everything running well on it including Urban Terror.


.

---

### Post by myromance123 on 2013-04-20
> **3dmatrix said:**
> Thanx, I will check these things one by one. But i will not be able to reply for two days. Anyway, if (in case) there is prob with Ubuntu then how do we check that ? I do not wish to reinstall Ubuntu again, its a big trouble updating and installing everything. And i have everything running well on it including Urban Terror.

You may or may not have broken packages (this is the only way I know of checking if Ubuntu is messed up or not). We can check and fix this by doing this in a Terminal:
```
sudo dpkg -a --configure
```

If everything on your system is fine, then we can safely assume this is a problem with Steam and its installer itself at the moment.

---

### Post by 3dmatrix on 2013-04-20
When you mentioned that hidden folder i checked it up and found two files (among others) whose content i am pasing here :

**registry.vdf**

"Registry"
{
	"HKLM"
	{
		"Software"
		{
			"Valve"
			{
				"Steam"
				{
					"InstallPath"		"/home/user/.local/share/Steam/"
					"SteamPID"		"0"
					"TempAppCmdLine"		""
					"TempAppPath"		""
				}
			}
		}
	}
	"HKCU"
	{
		"Software"
		{
			"Valve"
			{
				"Steam"
				{
					"Language"		"english"
					[B]"OfflineAFS"		"0"
					"Offline"		"0"[/B]
				}
			}
		}
	}
}

What abt that offline status ?


**steam.pid**

5670


.

---

### Post by Ranko Kohime on 2013-04-26
I'm having the same problem as the OP, I'm running 12.04, 32-bit, and the update downloader pops up for a brief time, not long enough to read, then it gives me the error that I'm offline.

Oddly enough, I had no troubles getting Steam to run on my 64-bit system.  ia32 libs should not be required for a 32-bit Ubuntu install, should they?

---

### Post by myromance123 on 2013-04-26
> **Ranko Kohime said:**
>  ia32 libs should not be required for a 32-bit Ubuntu install, should they?

Nope, it shouldn't. I just installed Steam on my system in Ubuntu 13.04 32Bit and it works fine. Since you mentioned that the updater pops up then just disappears, this could be an issue with the ClientRegistry.Blob (a common issue on Windows and Mac as well).

Can you head to .local/share/Steam and delete ClientRegistry.blob, then retry running Steam again. If you're worried about deleting ClientRegistry.blob, then you can just move it to your desktop as a backup (Steam will automatically redownload this file no matter how many times you delete it).

Does this get you further, or does the issue still persist?

---

### Post by Ranko Kohime on 2013-04-28
I cannot find a ClientRegistry.Blob, nor even a file with "client" in the name, upper or lower case, in the whole of my ~/

ETA: Here's the terminal output when I run 'steam'
```
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Assert( Assertion Failed: Illegal termination of worker thread 'Thread(0x0x8b577c8/0x0xb5e5bb4' ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier0/threadtools.cpp:2913

Installing breakpad exception handler for appid(steam)/version(1.0_client)
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2013-04-28 13:48:46] Startup - updater built Apr 19 2013 12:00:04
[2013-04-28 13:48:46] Verifying installation...
[2013-04-28 13:48:46] Unable to read and verify install manifest /home/ranko/.local/share/Steam/package/steam_client_ubuntu12.installed
[2013-04-28 13:48:46] Verification complete
[2013-04-28 13:48:46] Downloading Update...
[2013-04-28 13:48:46] Checking for available update...
[2013-04-28 13:48:47] Package file strings_all.zip.039f20af03325d88bf0e36525ef5785c6f1a635d missing or incorrect size
[2013-04-28 13:48:47] Package file resources_all.zip.7ad672422490098819d39d10a4bc494d3d28fc7f missing or incorrect size
[2013-04-28 13:48:47] Package file tenfoot_all.zip.dd0aeaf370bc542b087a4c1c9c9ca4a724fe0de3 missing or incorrect size
[2013-04-28 13:48:47] Package file tenfoot_fonts_all.zip.06551e23c14845665e7671feb9453b3ca1052939 missing or incorrect size
[2013-04-28 13:48:47] Package file tenfoot_ambientsounds_all.zip.ac31503c42f094976f64844d8ff54705cadc7dd3 missing or incorrect size
[2013-04-28 13:48:47] Package file tenfoot_sounds_all.zip.e8cce9ed600fc09e4a3f510fc3595d515bba6cd6 missing or incorrect size
[2013-04-28 13:48:47] Package file tenfoot_images_all.zip.b4b49c07ae879243999e3ce550be262075c18fe6 missing or incorrect size
[2013-04-28 13:48:47] Package file public_all.zip.5281a22558c77a31e1595fcacc35c24a359bdcfd missing or incorrect size
[2013-04-28 13:48:47] Package file bins_ubuntu12.zip.bc6b7a651c4ccd9131083e4152733fc849963b62 missing or incorrect size
[2013-04-28 13:48:47] Package file webkit_ubuntu12.zip.381e75bfc3340cf5eae9d265abb6de501f393f18 missing or incorrect size
[2013-04-28 13:48:47] Package file miles_ubuntu12.zip.9c547c676be26625a4cd64c2595821d10b8fc9ff missing or incorrect size
[2013-04-28 13:48:47] Package file sdl2_ubuntu12.zip.d09a45e506ed4296c18ccb33138bef0a66b88101 missing or incorrect size
[2013-04-28 13:48:47] Package file steam_ubuntu12.zip.df78d92661918e373815d48479e98ca5cd9dd125 missing or incorrect size
[2013-04-28 13:48:47] Package file runtime_part0_ubuntu12.zip.5de61e24414099bc83a812a4eb4da4781d60d6fe missing or incorrect size
[2013-04-28 13:48:47] Package file runtime_part1_ubuntu12.zip.07f2d2b01bc3521f709cba74aa0a9915dbb249b1 missing or incorrect size
[2013-04-28 13:48:47] Downloading update (0 of 155,073 KB)...
[2013-04-28 13:48:47] Error: Download of package (runtime_part0_ubuntu12) failed after 0 bytes (0).
[2013-04-28 13:48:47] Download Complete.
[2013-04-28 13:48:47] Error: Steam needs to be online to update.  Please confirm your network connection and try again.
[2013-04-28 13:48:49] Shutdown
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier0/threadtools.cpp (2913) : Assertion Failed: Illegal termination of worker thread 'Thread(0x0x8b577c8/0x0xb5e5bb4'
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20130428134850_1.dmp
Installing bootstrap /home/ranko/.local/share/Steam/bootstrap.tar.xz
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-2226f404-198a-4891-a9fb-1c5632130428
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME has been set by the user to: /home/ranko/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Installing breakpad exception handler for appid(steam)/version(1.0_client)
Assert( Assertion Failed: Illegal termination of worker thread 'Thread(0x0x8c6e7c8/0x0xb5f22b4' ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier0/threadtools.cpp:2913

Installing breakpad exception handler for appid(steam)/version(1.0_client)
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2013-04-28 13:48:53] Startup - updater built Apr 19 2013 12:00:04
[2013-04-28 13:48:53] Verifying installation...
[2013-04-28 13:48:53] Unable to read and verify install manifest /home/ranko/.local/share/Steam/package/steam_client_ubuntu12.installed
[2013-04-28 13:48:53] Verification complete
[2013-04-28 13:48:53] Downloading Update...
[2013-04-28 13:48:53] Checking for available update...
[2013-04-28 13:48:54] Package file strings_all.zip.039f20af03325d88bf0e36525ef5785c6f1a635d missing or incorrect size
[2013-04-28 13:48:54] Package file resources_all.zip.7ad672422490098819d39d10a4bc494d3d28fc7f missing or incorrect size
[2013-04-28 13:48:54] Package file tenfoot_all.zip.dd0aeaf370bc542b087a4c1c9c9ca4a724fe0de3 missing or incorrect size
[2013-04-28 13:48:54] Package file tenfoot_fonts_all.zip.06551e23c14845665e7671feb9453b3ca1052939 missing or incorrect size
[2013-04-28 13:48:54] Package file tenfoot_ambientsounds_all.zip.ac31503c42f094976f64844d8ff54705cadc7dd3 missing or incorrect size
[2013-04-28 13:48:54] Package file tenfoot_sounds_all.zip.e8cce9ed600fc09e4a3f510fc3595d515bba6cd6 missing or incorrect size
[2013-04-28 13:48:54] Package file tenfoot_images_all.zip.b4b49c07ae879243999e3ce550be262075c18fe6 missing or incorrect size
[2013-04-28 13:48:54] Package file public_all.zip.5281a22558c77a31e1595fcacc35c24a359bdcfd missing or incorrect size
[2013-04-28 13:48:54] Package file bins_ubuntu12.zip.bc6b7a651c4ccd9131083e4152733fc849963b62 missing or incorrect size
[2013-04-28 13:48:54] Package file webkit_ubuntu12.zip.381e75bfc3340cf5eae9d265abb6de501f393f18 missing or incorrect size
[2013-04-28 13:48:54] Package file miles_ubuntu12.zip.9c547c676be26625a4cd64c2595821d10b8fc9ff missing or incorrect size
[2013-04-28 13:48:54] Package file sdl2_ubuntu12.zip.d09a45e506ed4296c18ccb33138bef0a66b88101 missing or incorrect size
[2013-04-28 13:48:54] Package file steam_ubuntu12.zip.df78d92661918e373815d48479e98ca5cd9dd125 missing or incorrect size
[2013-04-28 13:48:54] Package file runtime_part0_ubuntu12.zip.5de61e24414099bc83a812a4eb4da4781d60d6fe missing or incorrect size
[2013-04-28 13:48:54] Package file runtime_part1_ubuntu12.zip.07f2d2b01bc3521f709cba74aa0a9915dbb249b1 missing or incorrect size
[2013-04-28 13:48:54] Downloading update (0 of 155,073 KB)...
[2013-04-28 13:48:54] Error: Download of package (runtime_part0_ubuntu12) failed after 0 bytes (0).
[2013-04-28 13:48:54] Download Complete.
[2013-04-28 13:48:54] Error: Steam needs to be online to update.  Please confirm your network connection and try again.
[2013-04-28 13:48:56] Shutdown
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier0/threadtools.cpp (2913) : Assertion Failed: Illegal termination of worker thread 'Thread(0x0x8c6e7c8/0x0xb5f22b4'
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20130428134857_1.dmp
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-d968deca-9a40-451c-a513-e8ef82130428

```

---

### Post by myromance123 on 2013-04-28
> I cannot find a ClientRegistry.Blob, nor even a file with "client" in the name, upper or lower case, in the whole of my ~/
That's definitely not normal. Is this Steam install from the Ubuntu Software Center? If it is, have you tried downloading the one from Steam's website(this is the one I always use)?

Something's gone bad with yours and 3dmatrix's install of Steam (probably due to how Steam was trying to update), but I can't figure out what. Usually a fresh reinstall of Steam will work, unless there's still remaining old files from previous Steam installs hiding around on your system.

---

### Post by Ranko Kohime on 2013-04-28
I don't have the Software Center installed on this particular machine, and I installed from the Steam .deb file.  This was also a first attempt at installing it on this particular machine, so no files should have been present beforehand.

---

### Post by myromance123 on 2013-04-29
I tried searching for possible solutions, and I found this: [LINK]("http://askubuntu.com/questions/256628/steam-fatal-error-steam-needs-to-be-online-to-update-but-was-set-to-offline-mov")

Basically, head to the .steam folder (it's hidden in your Home folder). Then delete the steam.pid file and .steampid file (there are two files, check carefully). Then, in a new Terminal install these
```
sudo apt-get install xfonts-100dpi xfonts-75dpi
```

Then try running Steam again, and if it doesn't work then just restart Ubuntu. Credits entirely go to elin3t on askubuntu for this solution.

---

### Post by Ranko Kohime on 2013-04-29
I wish I could say that worked, but unfortunately not.  I installed those two fonts, deleted ~/steam/steam.pid, ~/.steampid, and ~/.steam/starting, rebooted, and tried again, same result.  :(

---

### Post by Ranko Kohime on 2013-04-30
Well, I seem to have fixed my problem, by cheating.  I already had Steam setup and running on another Linux machine, so I copied the ~/.local/share/Steam/ubuntu12_32 folder over to the machine having the issue, and I'm now logged into Steam on that machine.

Now my only problem is that Steam is too big for my 800x480 resolution.  :lol:

---

### Post by myromance123 on 2013-05-01
Smart move, I wouldn't have thought of trying that. Well, at least we know that Steam can fail on installing itself properly. 

> Now my only problem is that Steam is too big for my 800x480 resolution. 
Hahaha, I know how you feel there. I can't really use Steam on anything smaller than my current screen without losing visibility :)

---

### Post by 3dmatrix on 2013-05-04
I even upgraded to 13.04 but still it is not leting me log in.

---

### Post by 3dmatrix on 2013-09-25
After struggling for many months, finally i found out it was my firewall that was not letting Steam client access the server.
When i switch off my firewall everything works fine. When i switch it on nothing works.
Any suggession.

---

### Post by Azdour on 2013-09-25
Hi,

The following page lists the ports required by Steam:

[https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711](https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711)

---

### Post by 3dmatrix on 2013-09-25
Well, i know about those ports and it works when i open them. But i am not sure about the safety issues when we keep ports open in the firewall.
Is there any way to make things more secure but still have Steam working ?

---

### Post by Azdour on 2013-10-01
Hmmm.... the only way I can think of is to run a script before running Steam to open the ports, then when you close it to run another script to close those ports.  Without those open ports Steam will not work as you have seen.

Maybe someone else on the forum is clever enough to suggest a single script that opens the ports, runs steam, then when it detects steams has closed it closes the ports.  This is beyond my knowledge at the moment.

---

