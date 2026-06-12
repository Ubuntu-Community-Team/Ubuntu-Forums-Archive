---
title: "Apparently issue with 32 bit libraries"
date: 2024-04-12
forum: Gaming &amp; Leisure
---

### Post by semplicementerichard on 2024-04-12
Steam doesn't start some games. As I understand it, this is a known error, but the solution is ambiguous and different for everyone.
I can start some games safely, but others cannot, like Binding of Isaac in this case. And what you see below is the error.
I tried steam directly from the valve site, then I tried steam from flatpak (because I had heard it solved this problem) but nothing, the error persists.
The computer is an old Mac mini from 2012 and has never given any kind of problem with Ubuntu.
I had the same problem on Arch linux, and Binding of isaac would not open.


/bin/sh\0-c\0/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/reaper SteamLaunch AppId=250900 -- /home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/steam-launch-wrapper -- '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/steamapps/common/The Binding of Isaac Rebirth/run-x64.sh'\0
chdir "/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/steamapps/common/The Binding of Isaac Rebirth"
ERROR: ld.so: object '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
ERROR: ld.so: object '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/richard/.var/app/com.valvesoftware.Steam/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
WARNING: discarding _NET_WM_PID 84190 as invalid for X11 window - use specialized XCB_X11_TO_PID function!
WARNING: discarding _NET_WM_PID 84190 as invalid for X11 window - use specialized XCB_X11_TO_PID function!
Initializing Theora Playback Library (1.1)
  - libtheora version: Xiph.Org libtheora 1.2.0alpha 20100924 (Ptalarbvorm)
  - libvorbis version: Xiph.Org libVorbis 1.3.4
------------------------------------
Setting breakpad minidump AppID = 250900
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198064302711 [API loaded no]
Game 250900 created interface STEAMAPPLIST_INTERFACE_VERSION001 / AppList
Game 250900 created interface STEAMAPPS_INTERFACE_VERSION008 / Apps
Game 250900 created interface STEAMAPPTICKET_INTERFACE_VERSION001 / 
Game 250900 created interface STEAMHTMLSURFACE_INTERFACE_VERSION_003 / HTMLSurface
Game 250900 created interface STEAMHTTP_INTERFACE_VERSION002 / HTTP
Game 250900 created interface STEAMINVENTORY_INTERFACE_V001 / Inventory
Game 250900 created interface STEAMMUSICREMOTE_INTERFACE_VERSION001 / MusicRemote
Game 250900 created interface STEAMMUSIC_INTERFACE_VERSION001 / Music
Game 250900 created interface STEAMREMOTESTORAGE_INTERFACE_VERSION014 / RemoteStorage
Game 250900 created interface STEAMSCREENSHOTS_INTERFACE_VERSION003 / Screenshots
Game 250900 created interface STEAMUGC_INTERFACE_VERSION009 / UGC
Game 250900 created interface STEAMUNIFIEDMESSAGES_INTERFACE_VERSION001 / UnifiedMessages
Game 250900 created interface STEAMUSERSTATS_INTERFACE_VERSION011 / UserStats
Game 250900 created interface STEAMVIDEO_INTERFACE_V001 / Video
Game 250900 created interface SteamController004 / Controller
Game 250900 created interface SteamFriends015 / Friends
Game 250900 created interface SteamMatchMaking009 / Matchmaking
Game 250900 created interface SteamMatchMakingServers002 / MatchmakingServers
Game 250900 created interface SteamNetworking005 / Networking
Game 250900 created interface SteamUser017 / User
Game 250900 created interface SteamUser019 / User
Game 250900 created interface SteamUtils007 / Utils
Game 250900 created interface SteamUtils008 / Utils
Game 250900 method call count for IClientUserStats::RequestCurrentStats : 1
Game 250900 method call count for IClientUtils::RecordSteamInterfaceCreation : 25
Game 250900 method call count for IClientUtils::GetAppID : 28
Game 250900 method call count for IClientUser::GetAppOwnershipTicketExtendedData : 1
Game 250900 method call count for IClientUser::GetSteamID : 2
Uploaded AppInterfaceStats to Steam

---

### Post by hyperlinxe on 2024-04-12
Generally the proper method for installing steam is simply 

sudo dpkg --add-architecture i386
sudo apt update
sudo apt install steam (or sudo dpkg -i steam.deb if you got the installer from the steam website)

If you installed steam correctly, then from the looks of other people's reports online the game works flawlessly. Some people report a better experience using proton to run the windows version of the game, which is a custom wine package steam makes to run windows games on linux, some people report no problem at all using the native version of the game. 

This is the protondb page for your game, where people share their experience getting games to work on linux with steam.

[https://www.protondb.com/app/250900](https://www.protondb.com/app/250900)

Generally you want to make sure you install steam correctly, and check out people's advice online to get games working properly. If you could describe the errors you're having specifically, besides just providing a log, that would be helpful.

The flatpak for steam is nice for distributions that do not provide 32bit library support basically, otherwise you are going to want to stick with your distributions provided packages, through sudo apt install steam, or the program direct from it's original source, steam actually provides a .deb to use for debian/ubuntu, which is perfect to fit our needs.

The other consideration is what your overall configuration looks like. What's your graphics card? Graphics driver? Display server? Desktop environment? Did you install steam correctly? In what way are you trying to run the game?

---

### Post by semplicementerichard on 2024-04-13
problem solved! apparently it was Wayland's fault.
If I move the session to Xorg everything works perfectly and all games start without any problems.
I knew wayland still has some problems, but I didn't think to this extent. Anyway the important thing is that it works. But the thing remains curious.
Now I will try to do the same on my laptop with Arch Linux. I will let you know if the problem is solved there as well.

Edit.
@hyperlinxe
ProtonDb in this case is not needed. binding of Isaac has the official linux porting

---

### Post by hyperlinxe on 2024-04-13
Yea that's what they said on protondb! They have reports about other people's experiences there regardless of whether or not wine is needed or it has what is called native support.

We can see there for example, if anyone else has a problem playing the game with wayland.

edit.. and nobody reports problems with wayland, only whether or not they use wine to run it or try to run it natively.

---

### Post by semplicementerichard on 2024-04-13
I confirm what I said earlier. I tried starting the game with Xorg on my laptop with Arch. Same outcome. Now the game works

---

### Post by hyperlinxe on 2024-04-13
Do you know what graphics driver you are using with wayland/xorg? What graphics card you have? Because that is one of the main issues right now with wayland is the graphics card/driver combo, and how we configure our systems to use them.

oh you say you have a... "The computer is an old Mac mini" 

well yea you are going to find you have all sorts of unique problems compared to everyone else then with that.
I would recommend using xorg/x11 primarily in your situation, unless you can find alternate information for your
unique hardware/drivers.

---

### Post by Namal23 on 2024-04-26
I installed steam with the steam-installer package

```
sudo apt install steam-installer
```

It asks me directly to install nvidia-driver-libs:i386  but there is no such a package. I don't know whether this is the problem but some older games like Titan Quest, that were perfectly fine don't start at all or have massive performance issues! Newer games like Hitman or RE4 are fine.
I am using Xubuntu and it does not have wayland.

---

### Post by 909mjolnir on 2024-07-08
> **semplicementerichard said:**
> problem solved! apparently it was Wayland's fault.
If I move the session to Xorg everything works perfectly and all games start without any problems.
I knew wayland still has some problems, but I didn't think to this extent. Anyway the important thing is that it works. But the thing remains curious.
Now I will try to do the same on my laptop with Arch Linux. I will let you know if the problem is solved there as well.

Edit.
@hyperlinxe
ProtonDb in this case is not needed. binding of Isaac has the official linux porting

Even though I do pro audio instead of gaming, I'm interested in this.  
Us audio guys and you gamers have some computer issue things in common.  
I use WINE sometimes for pro audio softwares and I'm always trying to get better results from the audio buffers.  
Also, I remember when 32-bit support was dropped, just a few years ago, all of a sudden there were bugs and crashes.

---

