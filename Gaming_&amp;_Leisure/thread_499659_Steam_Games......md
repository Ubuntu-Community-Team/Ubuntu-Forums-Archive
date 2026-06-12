---
title: "Steam Games....."
date: 2007-07-12
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2007-07-12
So I Have steam working fine. HL2/HL/CS/NS/etc all work fine.

Anyone have any ideas how to get Lost Planet to play? I dld the demo and it installed w/out a problem. Doesn't run at all though.

---

### Post by cogadh on 2007-07-13
Brand new games tend to be the hardest to get running in Wine. I'm assuming that you already meet Lost Planet's somewhat hefty minimum requirements, so let's focus on Wine itself. Please post the output from the terminal that is produced when you run Lost Planet, that may help identify where the failure is occurring.

---

### Post by Harkainos on 2007-07-13
Sorry for the delay. Here is the output it give me:


fixme:shdocvw:ViewObject_SetAdvise (0xf948a10)->(1 00000002 0x13a3450)
fixme:shdocvw:PersistStreamInit_InitNew (0xf948a10)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf948a10)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf948a10)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xf948a10)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xf948a10)
fixme:shdocvw:OleObject_Close (0xf948a10)->(1)
err:module:import_dll Library WMVCore.DLL (which is needed by L"H:\\games\\valve\\steamapps\\common\\lost planet demo\\LostPlanetDX9.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\games\\valve\\steamapps\\common\\lost planet demo\\LostPlanetDX9.exe" failed, status c0000135

It gives me the same error when I run it from steam or wine LostPlanetDX9.exe command

---

### Post by cogadh on 2007-07-13
You can ignore all the "fixme" messages, those are just developer notes. The "err" messages on the other hand are an issue. 

If you have a Windows installation, look in C:\windows\system32 for the wmvcore.dll file and copy it to $HOME/.wine/drive_c/windows/system32. If you don't have a Windows install to copy from, search online for it, you may be able to download it.

After you have copied the file to Wine's system32 directory, run "winecfg" from the terminal and go to the Libraries tab. Add an override for wmvcore.dll, then try running the game again. There's no guarantee this will work, but it may remove the error and allow the game to launch.

---

### Post by Harkainos on 2007-07-13
Alright. I have all the dlls it give me and I wrote the override for all the dlls needed.

When it comes up it say 'Unsupported Pixel Shader: 1.4'

---

### Post by cogadh on 2007-07-14
Is that error from the terminal or is the game itself giving you that message?

---

### Post by Harkainos on 2007-07-14
This comes up in the wine window as the game is about to load.

---

### Post by cogadh on 2007-07-15
Run "winecfg" and go to the graphics tab. Under "Direct3D", make sure Vertex shader support is set to "Hardware" and check the box for "Allow pixel shader support...". If those are already set, try adding a registry key to allow use of GLSL (OpenGL Shader Language). that may correct the shader problem. Run "regedit" in the terminal and do the following:
[LIST=1]
[*]Navigate through the file tree to HKEY_CURRENT_USER/Software/Wine
[*]Right-click in the right panel and select New > Key
[*]Label the key "Direct3D" (no quotes)
[*]Right-click in the right panel again and select New > String Value
[*]Label the new string "UseGLSL" (again, no quotes)
[*]Double-click on the new string entry and enter "enable" under Value data (you guessed it, no quotes again)
[*]Quit out of regedit and try running the game.
[/LIST]
See attached screenshot if that sounded confusing.

BTW - I probably should have asked this sooner, but what version of Wine are you using?

---

### Post by Harkainos on 2007-07-15
It still gives me the same error. When I have it in windowed mode it pulls that error. if i have it in non windowed mode it says: Unsupported Resolution. 1240*(something)

---

### Post by cogadh on 2007-07-15
There should be a file called config.ini in the game's install directory. Open it with a text editor and look for a section something like this:
```
Resolution=1280x720
RefreshRate=60Hz
FullScreen=ON
```
The resolution and refresh rate entries may be different. Change them both to what you currently have your monitor set to. Try launching the game without windowed mode and see if the error comes up.

Also, you didn't answer last time, what version of Wine are you using?

---

