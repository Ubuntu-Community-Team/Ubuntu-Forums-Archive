---
title: "Steam issue in Ubuntu 18.04 LTS"
date: 2019-06-20
forum: Gaming &amp; Leisure
---

### Post by bnagle on 2019-06-20
Hi, new to the forums so hopefully this is the right place for this.

I have recently installed Ubuntu 18.04 LTS on a newly purchased Razer Blade 15 mid 2019 laptop.  Got video card drivers and everything working, but ran into an issue with steam.

Steam installs fine, and it runs, installs updates, and lets me log in, but immediately after log in it gives me an error "Could not connect to the Steam network" and exits.  My network connection is fine, and clearly steam CAN connect since I can log in.

I have tried installing it via apt-get and also from the steam-latest.deb but have the same issue in both cases. I also tried it on a completely clean install and it did the same thing.  Running steam via terminal to see the logs shows no errors, it just exits.  In addition I tried the same thing using Ubuntu 19.04 and had the same issue, yet I tried Manjaro for fun earlier and steam worked fine (but I want to use Ubuntu).  I also tried steam --reset but this just lets me log in again and installs updates but then fails with the same error.

If anyone has any ideas it would be greatly appreciated.

Console logs:
```
unning Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins potentially out-of-date, rebuilding...
Found newer runtime version for 64-bit libGLU.so.1. Host: 1.3.1 Runtime: 1.3.8004
Found newer runtime version for 64-bit libdbusmenu-glib.so.4. Host: 4.0.12 Runtime: 4.0.13
Found newer runtime version for 64-bit libopus.so.0. Host: 0.5.2 Runtime: 0.7.0
Found newer runtime version for 64-bit libdbusmenu-gtk.so.4. Host: 4.0.12 Runtime: 4.0.13
[2019-06-20 11:46:44] Startup - updater built Jun 17 2019 23:31:08
[2019-06-20 11:46:44] Verifying installation...
[2019-06-20 11:46:44] Unable to read and verify install manifest /home/bryan/.steam/package/steam_client_ubuntu12.installed
[2019-06-20 11:46:44] Verification complete
[2019-06-20 11:46:44] Downloading update...
[2019-06-20 11:46:44] Checking for available updates...
[2019-06-20 11:46:44] Downloading manifest: http://client-download.steampowered.com/client/steam_client_ubuntu12
[2019-06-20 11:46:45] Download complete.
[2019-06-20 11:46:45] uninstalled manifest found in /home/bryan/.steam/package/steam_client_ubuntu12 (1).
[2019-06-20 11:46:45] Extracting package...
[2019-06-20 11:46:51] Installing update...
[2019-06-20 11:46:54] Cleaning up...
[2019-06-20 11:46:54] Update complete, launching Steam...
[2019-06-20 11:46:54] Shutdown
Restarting Steam by request...
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/bryan/.steam/ubuntu12_32/steam-runtime
Pins up-to-date!
[2019-06-20 11:46:54] Startup - updater built Jun 17 2019 23:31:08
[2019-06-20 11:46:54] Verifying installation...
[2019-06-20 11:46:54] Verification complete
STEAM_RUNTIME_HEAVY: ./steam-runtime-heavy
[2019-06-20 11:48:19] Shutdown
```

---

### Post by oldos2er on 2019-06-20
Please install a supported version,  8.04 went EOL years ago.

---

### Post by kpatz on 2019-06-20
> **oldos2er said:**
> Please install a supported version,  8.04 went EOL years ago.Typo.  His logs show he's running **1**8.04.

---

### Post by mastablasta on 2019-06-21
have you tried troubleshooting this with valve? they are the ones providing Steam. not sure why you get the error, it worked fine for me and many others. are you using wired internet? does it make any difference?

---

### Post by bnagle on 2019-06-21
> **kpatz said:**
> Typo.  His logs show he's running **1**8.04.

Thanks for fixing the typo!

---

### Post by bnagle on 2019-06-21
> **mastablasta said:**
> have you tried troubleshooting this with valve? they are the ones providing Steam. not sure why you get the error, it worked fine for me and many others. are you using wired internet? does it make any difference?

Wired or wifi does not make a difference.   Good suggestion about Valve, I didn't think of posting this on the valve forms.  I went looking, apparently I'm not the only person with this issue:
[https://github.com/ValveSoftware/steam-for-linux/issues/6326](https://github.com/ValveSoftware/steam-for-linux/issues/6326)

According to that, a number of people think it is a kernel issue, but there is no consensus as to which kernal(s) are causing the problem.  I don't really want to try swapping kernels, though I might, I guess uKuu is the safest way with Ubuntu?

As a temporary workaround,  I was able to install steam via PlayOnLinux.  Its not ideal, I'd rather the native linux client, but it appears to work fully and the performance is fine for the games I'm interested in.  I will probably just wait and watch that thread to see if someone finds a solution or the issue is fixed by Valve.  Thanks!

---

### Post by CatKiller on 2019-06-21
According to [this article about it](https://www.phoronix.com/scan.php?page=news_item&px=Steam-Networking-Kernel-Woes), starting Steam with the **-tcp** option has helped some people. I've not had any issues myself.

---

### Post by oldrocker99 on 2019-06-24
You **did** install Steam from the repositories?```
sudo apt install steam
```

This is the **only** way to properly install Steam. IF you downloaded Steam from the webpage, you'll have to remove it and properly install it.

---

### Post by pascua28 on 2019-07-22
Might be this one: [https://www.phoronix.com/scan.php?page=news_item&px=Steam-Networking-Kernel-Woes](https://www.phoronix.com/scan.php?page=news_item&px=Steam-Networking-Kernel-Woes)

---

### Post by LwIh%*7 on 2019-07-24
Please make sure that you installed the graphics card drivers from the repository and steam as well if using nvidia do the following 

```

sudo apt-get install nvidia-driver-390 steam

```

This would install the required dependencies, however, I'm not sure how to do it for the AMD-based graphics card as mine are NVIDIA-based. Also if you do get steam to work and the downloads fluctuate use unbound in NetworkManager.conf and re-generate the resolv.conf file so that it'll be generated by the Network Manager don't use the recommended dnsmasq as that I found didn't work correctly even with the recommended configuration.

Edit: Once the Graphics card driver is installed you might have to re-download the runtime libraries for steam so do rm -R .steam so that the steam folder in your home folder is removed then it'll re-download the entire library again but with the up-to-date configuration and should technically load then.

---

### Post by rakivilsov on 2019-08-21
> **bnagle said:**
> Hi, new to the forums so hopefully this is the right place for this.

I have recently installed Ubuntu 18.04 LTS on a newly purchased Razer Blade 15 mid 2019 laptop.  Got video card drivers and everything working, but ran into an issue with steam.

Steam installs fine, and it runs, installs updates, and lets me log in, but immediately after log in it gives me an error "Could not connect to the Steam network" and exits.  My network connection is fine, and clearly steam CAN connect since I can log in [COLOR=#000000][FONT=Arial]**[[color=#000000]xender[/color]](https://xender.vip/) [[color=#000000]discord[/color]](https://discord.software/) [[color=#000000]omegle[/color]](https://omegle.onl/)**[/FONT][/COLOR].

I have tried installing it via apt-get and also from the steam-latest.deb but have the same issue in both cases. I also tried it on a completely clean install and it did the same thing.  Running steam via terminal to see the logs shows no errors, it just exits.  In addition I tried the same thing using Ubuntu 19.04 and had the same issue, yet I tried Manjaro for fun earlier and steam worked fine (but I want to use Ubuntu).  I also tried steam --reset but this just lets me log in again and installs updates but then fails with the same error.

If anyone has any ideas it would be greatly appreciated.

Console logs:
```
unning Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins potentially out-of-date, rebuilding...
Found newer runtime version for 64-bit libGLU.so.1. Host: 1.3.1 Runtime: 1.3.8004
Found newer runtime version for 64-bit libdbusmenu-glib.so.4. Host: 4.0.12 Runtime: 4.0.13
Found newer runtime version for 64-bit libopus.so.0. Host: 0.5.2 Runtime: 0.7.0
Found newer runtime version for 64-bit libdbusmenu-gtk.so.4. Host: 4.0.12 Runtime: 4.0.13
[2019-06-20 11:46:44] Startup - updater built Jun 17 2019 23:31:08
[2019-06-20 11:46:44] Verifying installation...
[2019-06-20 11:46:44] Unable to read and verify install manifest /home/bryan/.steam/package/steam_client_ubuntu12.installed
[2019-06-20 11:46:44] Verification complete
[2019-06-20 11:46:44] Downloading update...
[2019-06-20 11:46:44] Checking for available updates...
[2019-06-20 11:46:44] Downloading manifest: http://client-download.steampowered.com/client/steam_client_ubuntu12
[2019-06-20 11:46:45] Download complete.
[2019-06-20 11:46:45] uninstalled manifest found in /home/bryan/.steam/package/steam_client_ubuntu12 (1).
[2019-06-20 11:46:45] Extracting package...
[2019-06-20 11:46:51] Installing update...
[2019-06-20 11:46:54] Cleaning up...
[2019-06-20 11:46:54] Update complete, launching Steam...
[2019-06-20 11:46:54] Shutdown
Restarting Steam by request...
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/bryan/.steam/ubuntu12_32/steam-runtime
Pins up-to-date!
[2019-06-20 11:46:54] Startup - updater built Jun 17 2019 23:31:08
[2019-06-20 11:46:54] Verifying installation...
[2019-06-20 11:46:54] Verification complete
STEAM_RUNTIME_HEAVY: ./steam-runtime-heavy
[2019-06-20 11:48:19] Shutdown
```
[COLOR=#000000]I was able to install steam via PlayOnLinux. Its not ideal, I'd rather the native linux client, but it appears to work fully and the performance is fine for the games I'm interested in. I will probably just wait and watch that thread to see if someone finds a solution or the issue is fixed by Valve. Thanks![/COLOR]

---

### Post by mastablasta on 2019-09-09
this would really be a question for valve support. they would know what the messages mean. i just installed it from software center and it worked.

it seems strange to me that this would be a hardware issue, since the messages don't indicate that. they do indicate that some newer libraries are available.

---

### Post by Dev'olution on 2019-09-11
```
[2019-06-20 11:46:44] Unable to read and verify install manifest /home/bryan/.steam/package/steam_client_ubuntu12.installed
[2019-06-20 11:46:44] Verification complete
[2019-06-20 11:46:44] Downloading update...
[2019-06-20 11:46:44] Checking for available updates...
[2019-06-20 11:46:44] Downloading manifest: http://client-download.steampowered.com/client/steam_client_ubuntu12
[2019-06-20 11:46:45] Download complete.
[2019-06-20 11:46:45] uninstalled manifest found in /home/bryan/.steam/package/steam_client_ubuntu12 (1).
```

```
[2019-06-20 11:46:54] Startup - updater built Jun 17 2019 23:31:08
[2019-06-20 11:46:54] Verifying installation...
[2019-06-20 11:46:54] Verification complete
STEAM_RUNTIME_HEAVY: ./steam-runtime-heavy
[2019-06-20 11:48:19] Shutdown
```

These two sections are interesting. It would seem that perhaps there is some sort of file sync issue about the installed files on the client and server?

Again, as above, would recommend supplying a ticket to Valve themselves about this.

---

### Post by mastablasta on 2020-04-29
> **wassfy said:**
> I simply got a server and i’m looking to install steam but while i am getting to steams internet site and click down load it says the report is 0kb


this is a completely different issue. there should be a deb file available, but you can install steam from software center.
> 
Additionally where am i able to find a listing of the games well suited with ubuntu 18.04

thanks, [[COLOR=#000000]GBWhatsApp[/COLOR]]("https://whatsappgb.download/")

you mean in Steam? 2 options here:
1. you just go to Steam shop and filter games by OS. the ones that says Steam OS work on 18.04. you just purchase them, install them, then run them.
2. you go to protondb.com and see which windows games will work if you use Steam proton. Gold or Platinum rating will means they work well.

need more games? check software center, snap store, or google for opensource linux games. You will also find some linux games on GOG. many GOG windows games will work well in proton, playon linjux or wine. 

Lutris is another launcher that makes windows games work on linux. be sure to read how it works and any caveats.

---

### Post by oldrocker99 on 2020-04-29
The **ONLY** way to properly install Steam is from the repositories:
```
sudo apt install steam
```

There are thousands of games which run on Steam for Linux, both native Linux games, and, with Steam Play and Proton, another 5,000+ games for Windows that also run.

---

