---
title: "Steam crashes at boot"
date: 2014-10-28
forum: Gaming &amp; Leisure
---

### Post by timonoj on 2014-10-28
Hi guys,

I am running Elementary OS Freya (Ubuntu 14.04 based), and my steam worked beautifully before on 12.10 to 13.10, but I don't seem to be able to make it work now.  I have an nvidia 755M SLI, with currently installed driver nvidia-331-updates. I attempted to install steam both from apt-get install steam, and the steam_latest.deb from the website.

I don't even get to the login screen, it crashes before. This is the log from launching steam from the console:
```

timonoj@Timo-PC:~/Downloads$ steam
Running Steam on elementary os 0.3 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steamwebhelper)/version(20141020140456)
Installing breakpad exception handler for appid(steamwebhelper)/version(1413813896)
[1028/220219:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20141020140456)
Installing breakpad exception handler for appid(steamwebhelper)/version(1413813896)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
[1028/220219:ERROR:renderer_main.cc(227)] Running without renderer sandbox
[1028/220219:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20141028220217_1.dmp
/home/timonoj/.local/share/Steam/steam.sh: line 729:  4528 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
[1028/220220:WARNING:content_browser_client.cc(499)] No browser info matching frame process id 1 and routing id 1
[1028/220220:WARNING:content_browser_client.cc(499)] No browser info matching frame process id 2 and routing id 1
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
Finished uploading minidump (out-of-process): success = no
error: Couldn't connect to server

```

Anyone can give me a hand? Thanks a lot!

---

### Post by dannyboy79 on 2014-10-28
i would suggest completely removing steam using your package manager, then ensure everything in your home directory has no remains of anything steam related, like delete this file if it's there 
```
/home/timonoj/.local/share/Steam/steam.sh
```
IMPORTANT: if you have games installed in your steam client they will get deleted as they're stored within your home directory normally (unless you choose to install them elsewhere). if you don't want to have redownload them all you could temporarily move them to another folder in /media/ or /mnt/ or anywhere other than ~/.steam or ~/.local/share/Steam). this is just a precaution in case you don't want to remove all your games because i'm suggesting you remove evertthing from ~/.steam/ OR ~/.Steam. games you purchased will still be able to be redownloaded if you do choose to delete them don't worry
then download steam from here [http://media.steampowered.com/client/installer/steam.deb](http://media.steampowered.com/client/installer/steam.deb)  and try to install it using
the command-line, use gdebi. Install the gdebi-core package (apt-get install gdebi-core) and then install the Steam for Linux package (gdebi steam.deb)

---

### Post by timonoj on 2014-10-28
Thanks for your help dannyboy79! I'll try with gdebi, I was using dpkg. I'll remove any traces of the steam installation, there's no issue as I just started a brand new OS installation.

---

### Post by timonoj on 2014-11-01
Hmm...Tried your way, and I still get the same crash. Any suggestions/ideas?

THanks a lot!

---

### Post by ranirahn on 2014-12-22
I have Lubuntu 14.04 32bit and i have same problem. Login box appears and then its completly frozen. I tried reinstalling by purge steam and steam-launcher and deleting ~/.steam and ~/.local/share/Steam folders. Changed VGA drivers to NVIDIA and X.Org but this did not change anything. I really need to know how to get it working again.

EDIT: Purged NVIDIA and wine installs and installed again and now looks like all works fine.

---

