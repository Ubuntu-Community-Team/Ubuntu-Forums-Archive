---
title: "Ubuntu server dedicated problem with Wine"
date: 2014-12-03
forum: Gaming &amp; Leisure
---

### Post by asd9 on 2014-12-03
I have Ubuntu server dedicated on VPS. I'm trying to start an server via PuTTY for a game of Steam, but when I start the server via Wine gives me this error:
```
Application tried to create a window, but no driver could be loaded.Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
fixme:thread:SetThreadIdealProcessor (0x130): stub
ERR:   Executable signature verification failed.
LOG:   Loaded "Z:\root\steam\samhd\Bin\GameEnv_Steam.dll".
INF:   GameEnv API: Steam
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005800, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005800, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005800, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005800, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005800, 0x3f036bc8, 0x3f036bc0
Setting breakpad minidump AppID = 41010
err:pulse:pulse_contextcallback Context failed: Connection refused
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
LOG:   Loaded "Z:\root\steam\samhd\Bin\SeriousSamHD_TSE_Project.dll".
LOG:     Content/SeriousSamHD_TSE/All_126138.gro: 836 files, signature: OFFICIAL
LOG:     Content/SeriousSamHD_TSE/All_208679.gro: 104 files, signature: OFFICIAL
LOG:     Content/SeriousSamHD_TSE/All.gro: 8476 files, signature: OFFICIAL
LOG:     Content/SeriousSamHD_TSE/CachedShaders_PC.gro: 6176 files, signature: OFFICIAL
LOG:     Content/SeriousSamHD_TSE/All_121332.gro: 207 files, signature: OFFICIAL
LOG:     Content/SeriousSamHD_TSE/DLC_PlayerModelsC.gro: 2 files, signature: OFFICIAL
fixme:dbghelp:elf_search_auxv can't find symbol in module
WRN:   Invalid locale string.
LOG:   Loading translation tables from Content/SeriousSamHD_TSE/Locales/enu/.
LOG:     Content/SeriousSamHD_TSE/Locales/enu/translation.tbl
LOG:   2014/12/01 20:33:53: Crashed! (used process memory: 0 MB, free system memory: 1988 MB)
ERR:   sysStartProcess("Z:\root\steam\samhd\Bin\BugReporter_Win32.exe") - 'No such file or directory'
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x9e0e62
```
Can anyone help me for this?

It runs on:
Ubuntu 12.04
Wine 1.6.1

---

### Post by dannyboy79 on 2014-12-03
i'm a little confused, you're using ubuntu "server" but trying to launch serious sam hd? you can see the first error is "Application tried to create a window, but no driver could be loaded" and it's saying you don't have a X server running. the X server is required because that's what's used to launch GUI's (graphical user interface's). you need a desktop environment for gaming, install either ubuntu, kubuntu, xubuntu, or lubuntu if you want to stick with ubuntu. you can do that even though you started with ubuntu server by installing either ubuntu-desktop, kubuntu-desktop, xuubntu-desktop, or lubuntu-desktop.

---

### Post by SirMoo on 2014-12-03
What? No. I think you're confusing what you need to do.

I'm going to assume you're trying to create a multi player server using SteamCMD. 

Try following the Garry's Mod server install instructions (they're easy to read and understand). [http://wiki.garrysmod.com/page/Linux_Dedicated_Server_Hosting](http://wiki.garrysmod.com/page/Linux_Dedicated_Server_Hosting) 

When you get to the part where you make the update_gmod.sh look for the number **4020** and replace it with **41080** which is the ID for a Serious Sam 3 Dedicated server. 

The command to start the server will be different than the instructions above... But this should get you on the way to having it properly installed. 

Wine shouldn't be involved since the game is native for Linux.

---

