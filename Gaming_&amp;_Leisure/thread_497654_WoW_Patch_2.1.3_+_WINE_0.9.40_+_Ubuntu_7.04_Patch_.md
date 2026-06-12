---
title: "WoW Patch 2.1.3 + WINE 0.9.40 + Ubuntu 7.04: Patch Install Problem"
date: 2007-07-10
forum: Gaming &amp; Leisure
---

### Post by Skylara on 2007-07-10
I've scoured the forums both here and at the Wine site and can't seem to find anything to fit my particular problem.  Hopefully someone here can help me out...

I run a Linux-only machine under Ubuntu 7.04 Feisty.  I have Wine installed, as well as World of Warcraft running under it, plus I have an NVidia card and use Envy to update it.

The problem I am having is that for about the last week or so, I've had to kill my Wine processes using the terminal because WoW would completely lock up on exit.  This happened to me before and was an addon issue, so I assumed the same and just kept killing it until I had time to sit down and sort through my addons to find the culprit.  I wasn't too very concerned, because the last two patches had downloaded just fine for me before the lockups started, and even after they started, the game was still playing wonderfully for me, with the exception of when I quit the game.

With today's WoW patch (2.1.3), I would log in, be prompted to exit to get the patch, the dowloader would pop up, then nothing... most likely because WoW would hang behind it, not closing, and lock up all my Wine processes.  So I moved all of my addons, my WTF folder and my WTB folder to a backup folder and tried again.  Same problem.  Hmmm...

So then I went to check on a driver update from Envy.  There was one, so Envy did its thing.  I also checked for a Wine update, as I was on 0.9.34.  0.9.40 was out so I updated to that.

Then back to the next attempt to get my WoW Patch.  Game loaded, it prompted me to close to download the patch, the downloader came up, the game closed and the download progressed. SUCCESS!

Well once the download was complete, I clicked "Finished" and at that point, the patch installer should have popped up to install said patch.  Nope.  I checked the program file and the patch was there, so I tried to manually start the install with a double-click.  Nope.  Well drat it... so I tried a Right Click and open with "Wine Windows Emulator."  Nope.

I thought perhaps my new Wine update was bad, so I tried to use the "open with" on the patch downloader, located in the same file as the patch.. both being .exe files.  Well, the downloader opened just fine and downloaded the patch yet again.

Frustrated, I just tried running the patch install from a terminal.  It seemed to work fine, but when I opened WoW, it didn't recognize that a patch had been installed and tried to download it again.  Eh?!  So I check the patch notes text file which the patch install updates and no listing for patch 2.1.3.

Grrr...

So I'm a bit stumped as to what to do now.  I'm not anywhere near to being a Linux/Ubuntu/WINE expert, so if someone can help me and needs more information, just let me know what you need and how I get it.

Thanks in advance for looking at this problem.

Edit: I just tested my double-click and right click on older patches in the same folder and they open fine.  Of course I get a message telling me I don't need to install them, but the point is, using Wine to open the patches to be installed works... just not on patch 2.1.2 > 2.1.3.
 
/commence banging head on desk

---

### Post by Sammi on 2007-07-10
Hmmm... what directory did you run the patch .exe from?

---

### Post by Skylara on 2007-07-10
> **Sammi said:**
> Hmmm... what directory did you run the patch .exe from?

From the directory all of the patches that have previously worked just fine are in...  /home/(myusername)/.wine/drive_c/Program Files/World of Warcraft\

---

### Post by Skylara on 2007-07-10
I just noticed that when I double-click, right-click, pray to the WoW gods to install the patch, two folders with various files in them appear in my Windows/temp folder.

Blizzard Installer Bootstrap (random number string)
Blizzard Installer Temporary Data (random number string)

So SOMETHING is happening with it when I click, but it never installs. So I go into the Bootstrap folder, click on Installer.exe, and it tells me "There is no patch file to apply."

---

### Post by mattwv on 2007-07-10
I am having the same problem, with the patch downloaded from multiple sources, so it shouldn't be a corrupt download.  Here are the results from trying to patch from the terminal.

```
 wine wow-2.1.2.6803-to-2.1.3.6898-enus-patch.exe
fixme:powrprof:DllMain (0x7d650000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d650000, 0, (nil)) not fully implemented
fixme:shdocvw:PersistStorage_InitNew (0x1a3dd0)->(0x4ff990)
fixme:shdocvw:WebBrowser_QueryInterface (0x1a3dd0)->({0000011e-0000-0000-c000-000000000046} 0x34f248) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x1a3dd0)->(L"My Host Name", (null))
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1a3e64)->((null) 1 0x34ef58 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1a3e64)->((null) 25 2 0x34ef6c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1a3e64)->((null) 26 2 0x34ef6c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1a3e64)->(0x34efa8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1a3e64)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34f054 (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x1a4d08)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1a4d68)
wine: Unhandled page fault on read access to 0x00000000 at address 0x7d470afc (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7d470afc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d470afc ESP:0034f0cc EBP:0034f104 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d4a0ca0 ECX:00110020 EDX:00000000
 ESI:800c0005 EDI:001a4d08
Stack dump:
0x0034f0cc:  001a4bb8 001a4bb8 00000000 7d49cacc
0x0034f0dc:  0034f0f4 7d50bfa8 001a3e94 7eb6c454
0x0034f0ec:  00000000 001a4bb8 00000000 7d4a0ca0
0x0034f0fc:  001a4a08 001a4478 0034f154 7d485f3c
0x0034f10c:  001a4d08 7d4a9b84 7d49b658 7d49b3a5
0x0034f11c:  001a4a08 00000000 001a4398 001a4478
Backtrace:
=>1 0x7d470afc start_binding+0xcc() in mshtml (0x0034f104)
  2 0x7d485f3c in mshtml (+0x45f3c) (0x0034f154)
  3 0x7d4fc89a in shdocvw (+0xc89a) (0x0034f1f4)
  4 0x7d4fd9a3 navigate_url+0x243() in shdocvw (0x0034f234)
  5 0x7d505a49 in shdocvw (+0x15a49) (0x0034f274)
  6 0x004bb691 in installer (+0xbb691) (0x00000010)
  7 0x00000000 (0x00000000)
0x7d470afc start_binding+0xcc in mshtml: movl   0x0(%edx),%ecx
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  517000       Export          installer

[snip]

ELF     f7f11000-f7f2f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000d    0
0000000a (D) C:\windows\temp\Blizzard Installer Bootstrap - 0000015e\Installer.exe
        0000000e    0
        0000000b    0 <==
00000008 
        00000009    0
~/Desktop$ 

```

---

### Post by Skylara on 2007-07-10
That's basically what I get too?

Are you replying to my WoW thread?  lol

Have you seen any mention of a work around or Wine patch or anything to fix this?  I'm sort of clueless on this stuff.

Edit: Nevermind.  From a poster on the WoW forums: "Downgrading to Wine version 0.9.33 (from Ubuntu Feisty distribution) fixed the problem."

I'm going to try and downgrade to 0.9.39 first before going back that far, though.

---

### Post by mattwv on 2007-07-10
Well, I downgraded to 0.9.37 and the patch worked fine.  I'm on amd64 if it makes a difference, I'll probably bump it back up to 0.9.39 and leave it there until this gets sorted out.

---

### Post by Skylara on 2007-07-10
I went ahead and tried 0.9.39 and finally got it working wonderfully again!

Here's the final summary for anyone else that might come across this post and need the fix...

* There is an issue with Wine 0.9.40 that will not allow the user to run a WoW Patch installation. This is not yet a documented bug on the official Wine AppDB site.
* The workaround is to downgrade to Wine 0.9.39 (or below).
* To downgrade, use your terminal to uninstall your current version of Wine. This will NOT delete any of your files under Wine, just the Wine program itself.
* Install version 0.9.39.
* Restart the Patch installation.
* Play WoW!

I won't be updating to 0.9.40 until I see some documentation that it's been fixed.   

Note:  There is also a one-line command for the terminal that you can use to downgrade, but I don't remember what it was >.<

---

### Post by Sammi on 2007-07-11
A link to where you may find older versions of Wine:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Please note that I wrote *older* not *old*. New versions of Wine are released in a fixed two week interval. They are not bug-tested or anything. They are simply still images of the current state of alpha development, released in a simple, pre compiled, and easy to install deb package.

---

### Post by Jermski on 2007-07-12
Im on Dapper, Had the same prob. Downgrading to WINE ver. 09.39 allowed a successfull install of the patch.

---

### Post by Ardrias on 2007-07-13
Just wanted to say that I was on 7.04, running Wine 0.9.40 and had no problems at all with the patch... So must be something other than just Wine itself for those of you having problems.

---

### Post by Nkari on 2007-07-14
Same here, same versions of everything and patching is not a problem. 

I just can get into the world I have crashing issues, but patching works just great, just like it did on windows

---

### Post by meEIKEL on 2007-07-15
had the same problem.
reinstalled WoW and after the first 529MB the problem remains.
now i installed wine version 0.9.39 to, and it is installing now.
looking good atm.

---

### Post by Nkari on 2007-07-15
Wonder if the fact that I have burning crusade installed is making any difference to how things are working?

---

