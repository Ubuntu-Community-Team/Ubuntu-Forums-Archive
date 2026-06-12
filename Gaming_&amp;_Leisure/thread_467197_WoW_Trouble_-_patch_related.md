---
title: "WoW Trouble - patch related?"
date: 2007-06-07
forum: Gaming &amp; Leisure
---

### Post by saggio on 2007-06-07
Hi there everyone, I originally made this post in the WoW howto thread, but it seems to have been lost to the nether reaches of the forum, so I'm making me own thread. Below is the post that I made: 


I was able to get WoW to launch and download the patch after I installed/enabled the proprietary ATI driver. But when I was patching WoW it hanged - so I downloaded it again, and it said patching was successful. However, when I started the launcher.exe, "Play" was not an option (was greyed out). After I closed that, I attempted to start WoW.exe from the shell (running $: wine WoW.exe in the appropriate place) - but instead of starting, it gave me a whole bunch of gibberish and nothing happened.

So I restarted the computer and logged back in, with the intention of staring WoW via the launcher.exe - but when I clicked on the icon on the desktop, nothing happened. So I tried to start launcher.exe via the shell as I had attempted to start WoW.exe before. The same thing happened! The game didn't launch, instead I got a bunch of gibberish in the shell.

Do I need to post what was spat out of the shell?

My system specs:

ASUS K8N-E Deluxe
AMD64 3200+ (s754, the one with the 1meg cache)
1.5Gb RAM
ATi X850 PRO (AGP)
I don't know the version of the proprietary driver...I just enabled it in the restricted driver manager, after I updated the system.

Here is the stuff it spat out when I tried to execute the WoW.exe file from the shell (it does nothing when I click on the icon on the desktop): 
```
$ wine WoW.exe
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000048 at address 0x7e182349 (thread 0024), starting debugger...
Unhandled exception: page fault on read access to 0x00000048 in 32-bit code (0x7e182349).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e182349 ESP:0033f990 EBP:0033fa08 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7e1e6fe4 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f990:  00000000 00000000 00000000 00000000
0x0033f9a0:  00000010 00000010 ffffffff 00000002
0x0033f9b0:  000010ef 00000340 00000000 00000010
0x0033f9c0:  00000000 001688f4 001688f4 7ecb5604
0x0033f9d0:  00000000 00004f4b 00000000 7ec6cc2f
0x0033f9e0:  7ecbd300 00000000 00000010 00000010
Backtrace:
=>1 0x7e182349 X11DRV_GetBitmapBits+0x1c9() in winex11 (0x0033fa08)
  2 0x7ec4198d GetBitmapBits+0x18d() in gdi32 (0x0033fa68)
  3 0x7ed1936c CreateIconFromResourceEx+0x93c() in user32 (0x0033fb08)
  4 0x7ed19867 in user32 (+0x29867) (0x0033fb88)
  5 0x7ed1aa78 LoadImageW+0x368() in user32 (0x0033fc28)
  6 0x7e3ddcfb TOOLTIPS_Register+0x11b() in comctl32 (0x0033fca8)
  7 0x7e37b72a in comctl32 (+0x1b72a) (0x0033fcd8)
  8 0x7e3f3ca3 in comctl32 (+0x93ca3) (0x0033fcf8)
  9 0x7bc39075 call_dll_entry_point+0x15() in ntdll (0x0033fd18)
  10 0x7bc3ac3d in ntdll (+0x2ac3d) (0x0033fda8)
  11 0x7bc3b41d in ntdll (+0x2b41d) (0x0033fde8)
  12 0x7bc3b362 in ntdll (+0x2b362) (0x0033fe28)
  13 0x7bc3b362 in ntdll (+0x2b362) (0x0033fe68)
  14 0x7bc3b362 in ntdll (+0x2b362) (0x0033fea8)
  15 0x7bc3d42e LdrInitializeThunk+0x2be() in ntdll (0x0033ff08)
  16 0x7b8721ea in kernel32 (+0x521ea) (0x0033ffe8)
  17 0xb7ece897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e182349 X11DRV_GetBitmapBits+0x1c9 in winex11: call  *0x48(%eax)
Modules:
Module  Address                 Debug info      Name (86 modules)
PE      340000-3a9000   Deferred        divxdecoder
PE      400000-ceb000   Deferred        wow
PE      10000000-10090000       Deferred        fmod
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e0d8000-7e0ed000       Deferred        midimap<elf>
  \-PE  7e0e0000-7e0ed000       \               midimap
ELF     7e0ed000-7e105000       Deferred        msacm32<elf>
  \-PE  7e0f0000-7e105000       \               msacm32
ELF     7e105000-7e141000       Deferred        wineoss<elf>
  \-PE  7e110000-7e141000       \               wineoss
ELF     7e143000-7e148000       Deferred        libxfixes.so.3
ELF     7e148000-7e151000       Deferred        libxcursor.so.1
ELF     7e151000-7e157000       Deferred        libxrandr.so.2
ELF     7e157000-7e15f000       Deferred        libxrender.so.1
ELF     7e15f000-7e162000       Deferred        libxinerama.so.1
ELF     7e162000-7e1f0000       Export          winex11<elf>
  \-PE  7e170000-7e1f0000       \               winex11
ELF     7e28e000-7e2ae000       Deferred        libexpat.so.1
ELF     7e2ae000-7e2d9000       Deferred        libfontconfig.so.1
ELF     7e2d9000-7e2ed000       Deferred        libz.so.1
ELF     7e2ed000-7e358000       Deferred        libfreetype.so.6
ELF     7e358000-7e414000       Export          comctl32<elf>
  \-PE  7e360000-7e414000       \               comctl32
ELF     7e414000-7e509000       Deferred        shell32<elf>
  \-PE  7e430000-7e509000       \               shell32
ELF     7e509000-7e562000       Deferred        shlwapi<elf>
  \-PE  7e520000-7e562000       \               shlwapi
ELF     7e562000-7e581000       Deferred        mpr<elf>
  \-PE  7e570000-7e581000       \               mpr
ELF     7e581000-7e5c9000       Deferred        wininet<elf>
  \-PE  7e590000-7e5c9000       \               wininet
ELF     7e5c9000-7e61e000       Deferred        rpcrt4<elf>
  \-PE  7e5e0000-7e61e000       \               rpcrt4
ELF     7e61e000-7e6b8000       Deferred        ole32<elf>
  \-PE  7e630000-7e6b8000       \               ole32
ELF     7e6b8000-7e71f000       Deferred        msvcrt<elf>
  \-PE  7e6d0000-7e71f000       \               msvcrt
ELF     7e71f000-7e745000       Deferred        msacm32<elf>
  \-PE  7e730000-7e745000       \               msacm32
ELF     7e745000-7e762000       Deferred        imm32<elf>
  \-PE  7e750000-7e762000       \               imm32
ELF     7e762000-7e776000       Deferred        lz32<elf>
  \-PE  7e770000-7e776000       \               lz32
ELF     7e776000-7e78f000       Deferred        version<elf>
  \-PE  7e780000-7e78f000       \               version
ELF     7e78f000-7e794000       Deferred        libxdmcp.so.6
ELF     7e794000-7e814000       Deferred        libglu.so.1
ELF     7e814000-7e8b4000       Deferred        libgl.so.1
ELF     7e8b4000-7e9a5000       Deferred        libx11.so.6
ELF     7e9a5000-7e9b3000       Deferred        libxext.so.6
ELF     7e9b3000-7e9b8000       Deferred        libxxf86vm.so.1
ELF     7e9b8000-7e9d0000       Deferred        libice.so.6
ELF     7e9d0000-7ea51000       Deferred        opengl32<elf>
  \-PE  7e9f0000-7ea51000       \               opengl32
ELF     7ea51000-7ea64000       Deferred        libresolv.so.2
ELF     7ea64000-7ea82000       Deferred        iphlpapi<elf>
  \-PE  7ea70000-7ea82000       \               iphlpapi
ELF     7ea82000-7eaaf000       Deferred        ws2_32<elf>
  \-PE  7ea90000-7eaaf000       \               ws2_32
ELF     7eaaf000-7eac9000       Deferred        wsock32<elf>
  \-PE  7eac0000-7eac9000       \               wsock32
ELF     7eac9000-7eb0f000       Deferred        advapi32<elf>
  \-PE  7eae0000-7eb0f000       \               advapi32
ELF     7eb0f000-7eb1b000       Deferred        libgcc_s.so.1
ELF     7eb1b000-7eb1e000       Deferred        libxau.so.6
ELF     7eb1e000-7eb27000       Deferred        libsm.so.6
ELF     7ec11000-7ecce000       Export          gdi32<elf>
  \-PE  7ec30000-7ecce000       \               gdi32
ELF     7ecce000-7ee0a000       Export          user32<elf>
  \-PE  7ecf0000-7ee0a000       \               user32
ELF     7ee0a000-7ee99000       Deferred        winmm<elf>
  \-PE  7ee20000-7ee99000       \               winmm
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d54000-b7d5d000       Deferred        libnss_compat.so.2
ELF     b7d5e000-b7d62000       Deferred        libdl.so.2
ELF     b7d62000-b7ea3000       Deferred        libc.so.6
ELF     b7ea4000-b7ebb000       Deferred        libpthread.so.0
ELF     b7ec7000-b7fd8000       Export          libwine.so.1
ELF     b7fda000-b7ff5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000031 (D) C:\World of Warcraft\WoW.exe
        00000024    0 <==
00000040 
        0000001d    0
        00000020    0
        0000001c    0
        00000019    0
        00000012    0
        0000000f    0
        00000013    0
        00000042    0
        00000041    0

```

It doesn't make much sense to me - since I hadn't changed any video/sound settings between intially launching the game and downloading/installing the patch. What should I do? I'm really lost and I'd like to play my game...

Thanks.

---

### Post by hikaricore on 2007-06-07
> Xlib:  extension "XFree86-DRI" missing on display ":0.0"

This kinda stands out to me as odd.

Are you able to run other 3d applications after updating your system?  I think it may be a driver issue at the moment.

---

### Post by Cappy on 2007-06-07
Try this:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension)
Just the "Disable Composite Extension" section.

Also, make sure you turn off Beryl/Compiz when you run a game.

---

### Post by saggio on 2007-06-07
> **Cappy said:**
> Try this:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension)
Just the "Disable Composite Extension" section.

Also, make sure you turn off Beryl/Compiz when you run a game.

Just tried that. Nothing changed in the output. 

I don't use Beryl (at least I think I don't - haven't changed the default WM from whatever comes with Feisty Fawn and GNOME), but where would I go to enable/disable it if I did? 

Thanks.

---

### Post by Cappy on 2007-06-07
It would a GEM looking icon in the "Notification Area" (top right hand corner) OR (System-->Preferences-->Desktop Background).

[http://ubuntuforums.org/showthread.php?t=463089&highlight=XFree86-DRI+missing](http://ubuntuforums.org/showthread.php?t=463089&highlight=XFree86-DRI+missing)
It basically says to 
```

sudo gedit /etc/default/linux-restricted-modules-common

```
and replace the line that says ```
DISABLED_MODULES="flgrx"
``` or whatever it may say with just 
```
DISABLED_MODULES=""
```

---

### Post by saggio on 2007-06-07
> **Cappy said:**
> It would a GEM looking icon in the "Notification Area" (top right hand corner) OR (System-->Preferences-->Desktop Background).

[http://ubuntuforums.org/showthread.php?t=463089&highlight=XFree86-DRI+missing](http://ubuntuforums.org/showthread.php?t=463089&highlight=XFree86-DRI+missing)
It basically says to 
```

sudo gedit /etc/default/linux-restricted-modules-common

```
and replace the line that says ```
DISABLED_MODULES="flgrx"
``` or whatever it may say with just 
```
DISABLED_MODULES=""
```

Alright, I did that and I was able to launch the game and download the latest small patch. But now I don't have sound, and whenever I try to run WoW now I get this error:

```
This Application has encountered a critical error
ERROR #131 (0x85100083) File Corrupt
Program:     C:\World of Warcraft\WoW.exe
File:    DBFilesClient\Spell.dbc

Press OK to terminate the application.
```

---

### Post by Cappy on 2007-06-07
I googled on that and it is a lot of Windows users are getting that error with no known solution. You may just want to delete your ~.wine directory and completely reinstall. Unless you can find a copy of that file somewhere, I don't know what else there is to do.

---

### Post by saggio on 2007-06-07
> **Cappy said:**
> I googled on that and it is a lot of Windows users are getting that error with no known solution. You may just want to delete your ~.wine directory and completely reinstall. Unless you can find a copy of that file somewhere, I don't know what else there is to do.

Delete both Wine and WoW? Or just Wine?

---

### Post by hikaricore on 2007-06-07
Personally I would just delete the WoW directory if it's the problem..  deleting and reconfiguring wine is a bit of overkill.

Funny thing, I don't even have a Spell.dbc file.  It also doesn't seem to exist on my girl's system.  O.o

---

### Post by saggio on 2007-06-07
> **hikaricore said:**
> Personally I would just delete the WoW directory if it's the problem..  deleting and reconfiguring wine is a bit of overkill.

Funny thing, I don't even have a Spell.dbc file.  It also doesn't seem to exist on my girl's system.  O.o

Does WoW work for you, though? If it does, I don't see how Spell.dbc could be a problem. Hmm...

---

### Post by hikaricore on 2007-06-08
Yea it works fine on both systems.

I wish I could think of another way than removing & reinstalling WoW, but that's about it.

---

### Post by Sammi on 2007-06-08
One thing: If or when you reinstall WoW successfully, you might be interested in making a backup copy of the whole WoW directory, as it is a drop in replacement for the install cds, with the added benefit what you wont have to update WoW the whole way again, if the game ever becomes corrupt again. 

I really really like games that are self-contained in one folder. I think Blizzard always does this with their games.

Oh and I really really DON'T like EA games, because their games are never this pretty to install.

---

### Post by saggio on 2007-06-08
I reinstalled it, patched it, and the same thing is happening! Nothing happens when I click on the icon, and when I start WoW.exe from the shell ($ wine WoW.exe) it spits out the same stupid error message. 

Please help! I don't know what to do.

---

### Post by saggio on 2007-06-08
Does no one have any idea? Hasn't anyone  had this problem before? Is there something I can do to fix it? What can I try? I don't want to go back to Windows, but I'm not the only one who uses the computer, and the other user really wants to play WoW...

Please help! I'm a complete noob when it comes to this sort of thing.

---

### Post by Cappy on 2007-06-08
Like I said, no one knows a solution. You can google it and see if someone has found a solution. I just saw some threads on the WoW forums and said no one knows why.

---

### Post by saggio on 2007-06-08
> **Cappy said:**
> Like I said, no one knows a solution. You can google it and see if someone has found a solution. I just saw some threads on the WoW forums and said no one knows why.

There's nothing I can add to my xorg.conf? Because I think there is something wrong with the stupid ATi driver. The same thing is happening as happened intially, and I don't know why.

---

