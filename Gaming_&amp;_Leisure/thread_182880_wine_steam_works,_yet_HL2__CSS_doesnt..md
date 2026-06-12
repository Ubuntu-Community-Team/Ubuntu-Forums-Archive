---
title: "wine: steam works, yet HL:2 / CS:S doesnt. ?"
date: 2006-05-26
forum: Gaming &amp; Leisure
---

### Post by stanna on 2006-05-26
first i must mention that this is a fresh install of dapper, with all upto date updates included also.

i have wine installed, then getting all the fonts, activeX controls and mozcontrol something.. and instmsia or whatever its called. then steam is installed, then downloaded all the hl2 & cs:s files. and it all appears to be working correctly. i can run steam and it shows up and all that jazz, 

when i try to launch the actual game, it will load the initial loading image then just drop back to the desktop with my resolution changed to 1024x768.. has anyone else had something similair happen?  i have included a the log from the console i launched "wine steam.exe" from..., i dont know if it means anything, i have also tried launching it with -dxlevel 80 and -dxlevel 70 and neither make a difference where it says directX 9 is unavailable.. 

```

stanna@machine:~/.wine/drive_c/Program Files/Steam$ wine steam
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4590f811-1d3a-11d0-891f-00aa004b2e24}, hres is 0x80040154
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
wine: Call from 0x2a00c490 to unimplemented function d3d9.dll.D3DPERF_SetOptions, aborting
fixme:dbghelp:sffip_cb NIY on 'u:\projects\staging\src\launcher_main\Release\launcher_main.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\launcher\Release\launcher.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\vstdlib\Release\vstdlib.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\tier0\Release\tier0.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\filesystem\filesystem_stdio\Release_Steam\filesystem_steam.pdb'
fixme:dbghelp:sffip_cb NIY on 'u:\p4clients\rel_beta\Projects\GazelleProto\Client\Engine\VC70_Release_Static\SteamEngine.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\datamodel\Release\datamodel.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\dmserializers\Release\dmserializers.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\datacache\Release\datacache.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\inputsystem\Release\inputsystem.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\materialsystem\Release\materialsystem.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\studiorender\Release\studiorender.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\vphysics\Release\vphysics.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\avi\Release\valve_avi.pdb'
fixme:dbghelp:sffip_cb NIY on 'u:\rel\hl2\src\vguimatsurface\Release\vguimatsurface.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\vgui2\src\Release\vgui2.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\engine\GLRelease\engine.pdb'
fixme:dbghelp:sffip_cb NIY on 'c:\steam3_rel_client\src\steam_api\Release\steam_api.pdb'
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\materialsystem\shaderdx8\Release\shaderapidx9.pdb'
fixme:dbghelp:sffip_cb NIY on 'u:\p4clients\taylor_pubkeys\ThirdPartyCode\DebugNet\Release\BugslayerUtil.pdb'
wine: Call from 0x7fc0e770 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting
fixme:avifile:AVIFileExit (): stub!
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless


```

](*,)

---

### Post by Polygon on 2006-05-27
i have the same thing happen to me in ubuntu 5.10 (not that its gonna help you), it just loads the cs:s loading image, then crashes to desktop.

---

### Post by B0rsuk on 2006-05-28
I have found a promising HOWTO, but as I don't have the game, I can't test it. Have a look:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

If you solve it, please let us know. I'm interested in 'wining' one upcoming game on Source engine.

---

### Post by stanna on 2006-05-28
thats a nice link B0rsuk, thanks for that. ill check it out as soon as i can when i get home tonight. i was forced to make a little windowsXP partition once again just to place counter-strike. i was hoping to be linux only over the weekend, but i was forced back again :( but i will continue to try getting all this working.

thanks again, and ill get back to you as soon as i can. lets hope it works!

---

### Post by ubu-for on 2006-05-30
I have a similar problem since wine 0.9.14 or last CSS update (May 25).

```

wine: Call from 0x2a00c490 to unimplemented function d3d9.dll.D3DPERF_SetOptions, aborting
wine: Call from 0x7fc0eb30 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting

```

> 
I have found a promising HOWTO, but as I don't have the game, I can't test it. Have a look:

[http://www.linux-gamers.net/modules/...X+Wine+G](http://www.linux-gamers.net/modules/...X+Wine+G) ames


It's only a installation howto.

---

### Post by B0rsuk on 2006-05-30
[QUOTE=ubu-for]
It's only a installation howto.[/QUOTE]

From the very article you didn't care to read:

> 
Q: I'm on Ubuntu Breezy, SuSE 10.0 or another older distro with a kernel 2.6.14 or older. Steam randomly freezes.

Use uname -r to check your kernel version. If it's older than 2.6.15, upgrade to kernel 2.6.15 or newer.

**Q: Wine crashes with the following line: wine: Call from 0x404b1fa0 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting**

You have got the wrong mozilla control. **Read the howto more carefully**, especially the section 3.


---

### Post by mejy on 2006-06-06
[QUOTE=B0rsuk]From the very article you didn't care to read:[/QUOTE]
I followed the article exactly, and still get this error, although the "call from" part is different.  Did the original poster get this working?  This is using dapper so I'm not sure if I should start a new thread seeing how similar the error is.

---

### Post by stanna on 2006-06-06
> I followed the article exactly, and still get this error, although the "call from" part is different. Did the original poster get this working? This is using dapper so I'm not sure if I should start a new thread seeing how similar the error is.

mejy, i am running dapper.. when posting this i didnt have the option to say the exact ubuntu i was using.. anyway, i am still having the same problem even tho i have gone thru all guides and done exactly what is required. perhaps the download link is just the wrong file coz i keep getting the same error... kind of annoying, so i did have to resort to re-creating a minimal windowsXP partition just for steam alone, and i find myself using it more and more now, coz id do some web dev, play cs:s for an hour then continue to do some web work, eventualy i got sick of restarting constantly so im almost back to being a windows user, which is a shame really.

---

### Post by chrism66 on 2006-06-06
Ok this shows what a 'Newbi' that I am. How do I extract the mozila controls to the write protected ~/.wine/drive_c/ProgramFiles/? I have tried all my limted commands to get them installed. Any help would be greatlly appreciated!

Regards,
Chris

---

### Post by ubu-for on 2006-06-07
[QUOTE=B0rsuk]
From the very article you didn't care to read:

> Q: I'm on Ubuntu Breezy, SuSE 10.0 or another older distro with a kernel 2.6.14 or older. Steam randomly freezes.

Use uname -r to check your kernel version. If it's older than 2.6.15, upgrade to kernel 2.6.15 or newer.

Q: Wine crashes with the following line: wine: Call from 0x404b1fa0 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting

You have got the wrong mozilla control. Read the howto more carefully, especially the section 3.
[/QUOTE]

I didn't care to read?

Open your eyes! Your quote is not from this thread.

---

### Post by Polygon on 2006-06-08
[QUOTE=chrism66]Ok this shows what a 'Newbi' that I am. How do I extract the mozila controls to the write protected ~/.wine/drive_c/ProgramFiles/? I have tried all my limted commands to get them installed. Any help would be greatlly appreciated!

Regards,
Chris[/QUOTE]


double click the "mozcontrol.tgz" and it will open up an archive manager, and you will see the folder inside of it. simply drag this folder to your desktop , and it will extract the folder and its contents to the desktop

then, open up terminal

cd (change directory) to your desktop, 

```
cd Desktop
```

then, copy//paste in terminal

```
sudo mv mozcontrol ~/.wine/drive_c/Program\ Files/mozcontrol
```

and this will move the "mozcontrol" folder to your "fake" drive c

please note that in order to get to folders with spaces (like Program files) you have to have the backwards slash seperating them, like "Program\ Files".  Just something good to know for the future :D

---

### Post by echo $USER on 2006-06-08
I got HL2 playable, but not CS:S or DOD:S.

---

### Post by Jason_25 on 2006-06-08
Valve changed something in their latest update that caused wine/cedega to not work but recently a cedega update was released to fix the problem.  I can start CS:S  with cedega now but it stutters too much to play.

---

### Post by crankcaller on 2006-06-08
[QUOTE=Jason_25]  I can start CS:S  with cedega now but it stutters too much to play.[/QUOTE]

@r$e!   i'm downloading cs:s in steam just now as cedega wouldn't let me install my backup files...

might as well stop the download.  It doesn't run in XP coz of a problem with my processor/motherboard combo.  Same with Battlfield 2 ](*,) 

Back to Americas Army it is....

---

### Post by chrism66 on 2006-06-09
So I take it that it would be a waste of time ti install Wine to play CS-S? Sounds like Wine n Codeaga won't do it!

---

### Post by echo $USER on 2006-06-09
[QUOTE=chrism66]So I take it that it would be a waste of time ti install Wine to play CS-S? Sounds like Wine n Codeaga won't do it![/QUOTE]

CS and DOD work, but all the source games no, except for HL2 (but runs like crap).

---

### Post by Jason_25 on 2006-06-09
[QUOTE=chrism66]So I take it that it would be a waste of time ti install Wine to play CS-S? Sounds like Wine n Codeaga won't do it![/QUOTE]
Cedega works with all the source games.  But it's almost a waste because of the stuttering, random locking up.  I'm going to try it on a more powerful system but I'm afraid the results will be the same.

---

