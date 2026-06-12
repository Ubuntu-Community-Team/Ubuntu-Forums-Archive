---
title: "Steam won't start up + Cedega"
date: 2005-04-03
forum: Gaming &amp; Leisure
---

### Post by NateC on 2005-04-03
I installed Steam perfectly, and Cedega perfectly. I downloaded a few games, and then exited out of steam so I could reboot. After I rebooted I wanted to play Day Of Defeat. So, I went to the steam.exe a double clicked it so it would open with cedega, and when I do this I get an error :

> 
Steam.exe (main exception): Unable to change directory to /home/nathan/TransGaming_Drive/Program Files/Valve/Steam/
 


Does anyone know what to do? I would really like to get windows wiped off my hard-drive.

---

### Post by telmo on 2005-04-03
I want that too!!!  [-o<

---

### Post by seven on 2005-04-04
you should change your working directory to steam's one:
ive built an simpale script for this:

> cedega -workdir "/home/seven/TransGaming_Drive/Program Files/Valve/Steam" "/home/seven/TransGaming_Drive/Program Files/Valve/Steam/ppatcher.exe"

jsut run this script and Steam should run great 

*ofcurse dont forget to change the path to steam

---

### Post by telmo on 2005-04-04
[QUOTE=seven]you should change your working directory to steam's one:
ive built an simpale script for this:



jsut run this script and Steam should run great 

*ofcurse dont forget to change the path to steam[/QUOTE]

hmmm... i don't have any ppatcher.exe over here! :( Do i need it?

---

### Post by seven on 2005-04-06
replace the ppatcher.exe with steam.exe.
you don't need the ppatcher

---

### Post by telmo on 2005-04-07
I get the exact same error! 'Cannot change directory... bla bla bla...' And i tried ppatcher and it doesn't even run.  :-(
Guess i'm stuck with Windows...

---

### Post by NateC on 2005-04-08
Ummm, that doesn't seem to work... anybody else know what to do?

---

### Post by bored2k on 2005-04-08
For the record. By running ppatcher you could expose urself to getting ur account banned from steam. Trust me, I know about it.

---

### Post by telmo on 2005-04-08
whooo... i don't want that!!! I have a platinum key!
Thanks for the warning!

But, how the hell do i manage to run it (Steam)??? A HOWTO would be really nice!

---

### Post by NateC on 2005-04-08
Yeah really.. what would the specific link be for starting up steam?

---

### Post by fackamato on 2005-04-08
I'm using Cedega 4.3 on Hoary.

This starts steam, and hl1/2, cs1/source and whatever is in your game list:

```
cedega steam.exe
```

Make sure your ~/.transgaming/config is setup properly.

---

### Post by NateC on 2005-04-09
It's configured fully, and it still gives me that error.

---

### Post by fackamato on 2005-04-09
[QUOTE=NateC]It's configured fully, and it still gives me that error.[/QUOTE]

Then it's configured wrong, or you're doing something wrong, because it works here. Post your cedega config. Are you using cvs cedega or the commercial version?

---

### Post by NateC on 2005-04-09
I am using the commerical version.

---

### Post by NateC on 2005-04-09
WINE REGISTRY Version 2
;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;;
;; MS-DOS drives configuration
;;
;; Each section has the following format:
;; [Drive X]
;; "Path"="xxx"       (Unix path for drive root)
;; "Type"="xxx"       (supported types are 'floppy', 'hd', 'cdrom' and 'network')
;; "Label"="xxx"      (drive label, at most 11 characters)
;; "Serial"="xxx"     (serial number, 8 characters hexadecimal number)
;; "Filesystem"="xxx" (supported types are 'msdos'/'dos'/'fat', 'win95'/'vfat', 'unix')
;;   This is the FS Wine is supposed to emulate on a certain
;;   directory structure.
;;   Recommended:
;;   - "win95" for ext2fs, VFAT and FAT32
;;   - "msdos" for FAT16 (ugly, upgrading to VFAT driver strongly recommended)
;;   DON'T use "unix" unless you intend to port programs using Winelib !
;; "Device"="/dev/xx" (only if you want to allow raw device access)
;;
[Drive C]
"Path" = "/home/nathan/.transgaming/c_drive"
"Type" = "hd"
"Label" = "Dos Drive"
"Filesystem" = "win95"
 
[Drive D]
"Path" = "${HOME}"
"Type" = "hd"
"Label" = "My Home"
"Filesystem" = "win95"
 
[Drive E]
"Path" = "/tmp"
"Type" = "hd"
"Label" = "tmp"
"Filesystem" = "win95"
 
[Drive G]
"Path" = "/"
"Type" = "hd"
"Label" = "root"
"Filesystem" = "win95"

[wine]
"Windows" = "c:\\windows"
"System" = "c:\\windows\\system32\\"
"Temp" = "e:\\"
"Path" = "c:\\windows\\;c:\\windows\\system32\\"
"GraphicsDriver" = "x11drv" 
; Wine doesn't pass directory symlinks to Windows programs by default.
; Enabling this may crash some programs that do recursive lookups of a whole
; subdir tree in case of a symlink pointing back to itself.
;
; Note: The WINESHELLLINK Environment variable will override this setting.
;       (which is set in the winex startup script)
;"ShowDirSymlinks" = "1"
"ShellLinker" = "/usr/lib/transgaming_cedega/winex/bin/wineshelllink"
;
; Browser to be used by winebrowserlink.
; Note: The WINEBROWSER Environment variable will override this setting.
;"Browser" = "/usr/bin/konqueror"
;
; Use the mozilla control as the IE control where available
;"MozillaControl" = "Y"

# <wineconf>

[DllDefaults]
"DefaultLoadOrder" = "native, builtin, so"

[DllOverrides]
"commdlg"      = "builtin, native"
"comdlg32"     = "builtin, native"
"oleaut32"     = "builtin, native"
"ver"          = "builtin, native"
"version"      = "builtin, native"
"shell"        = "builtin, native"
"shell32"      = "builtin, native"
"shfolder"     = "builtin, native"
"shlwapi"      = "builtin, native"
"lzexpand"     = "builtin, native"
"lz32"         = "builtin, native"
"comctl32"     = "builtin, native"
"commctrl"     = "builtin, native"
"advapi32"     = "builtin, native"
"crtdll"       = "builtin, native"
"mpr"          = "builtin, native"
"winspool.drv" = "builtin, native"
"d3d8"         = "builtin, native"
"d3d9"         = "builtin, native"
"d3drm"        = "builtin, native"
"ddraw"        = "builtin, native"
"dinput"       = "builtin, native"
"dinput8"      = "builtin, native"
"dmusic"       = "builtin, native"
"dsound"       = "builtin, native"
"opengl32"     = "builtin, native"
"msvcrt"       = "native, builtin"
"rpcrt4"       = "native, builtin"
"msvideo"      = "builtin, native"
"msvfw32"      = "builtin, native"
"mcicda.drv"   = "builtin, native"
"mciseq.drv"   = "builtin, native"
"mciwave.drv"  = "builtin, native"
"mciavi.drv"   = "native, builtin"
"mcianim.drv"  = "native, builtin"
"msacm.drv"    = "builtin, native"
"msacm"        = "builtin, native"
"msacm32"      = "builtin, native"
"midimap.drv"  = "builtin, native"  
"wininet"      = "builtin, native"

[Version]
; Windows version to imitate. Valid versions are: 'win20', 'win30', 'win31', 'win95', 'win98', 'winme', 'nt351', 'nt40', 'win2000', 'winxp'
"Windows" = "win98"
; DOS version to imitate
;"DOS" = "6.22"

[x11drv]
; Number of colors to allocate from the system palette
"AllocSystemColors" = "100"
; Number of colors to copy from the default palette
"CopyDefaultColors" = "0"
; Use a private color map
"PrivateColorMap" = "N"
; Favor correctness over speed in some graphics operations
"PerfectGraphics" = "N"
; Color depth to use on multi-depth screens
;;"ScreenDepth" = "16"
; Name of X11 display to use
;;"Display" = ":0.0"
; Allow the window manager to manage created windows
"Managed" = "Y"
; Use a desktop window of the given size
;"Desktop" = "800x600"
; Use XFree86 DGA extension if present
; (make sure /dev/mem is accessible by you !)
"UseDGA" = "N"
; Use XShm extension if present
"UseXShm" = "Y"
; Enable DirectX mouse grab
"DXGrab" = "Y"
; Use XVidMode extension if present
"UseXVidMode" = "Y"
; Use XRandR extension if present
"UseXRandR" = "N"
; Create the desktop window with a double-buffered visual
; (useful to play OpenGL games)
"DesktopDoubleBuffered" = "Y"
; Code page used for captions in managed mode
; 0 means default ANSI code page (CP_ACP == 0)
"TextCP" = "0"
; Use this if you have more than one port for video on your setup 
; (Wine uses for now the first 'input image' it finds).
;; "XVideoPort" = "43"
; Use this to make your X server execute all commands
; sequentially rather than buffering commands. Will make
; everything really SLOW but can be nice for debugging.
;; "Synchronous" = "Y"
; Enable the FPS count on the TransGaming HUD (also activates the HUD)
;; "ShowFPS" = "Y"
; Enable memory statistics on the TransGaming HUD (must have ShowFPS activated)
;; "ShowMem" = "Y"
; How much Video RAM does your card have?
"VideoRam" = "32"
; How much AGP memory should be used for vertex data (about 1/2 your AGP aperature size)
"AGPVertexRam" = "32"
; Use NV_VAR (enabled by default)
;;"NV_VAR" = "Y"
; Use ARB_VBO (enabled by default, NV_VAR takes precendence)
;;"ARB_VBO" = "Y"


[d3dgl]
"AnisotropicTextureFiltering" = "N"
"VertexShaders" = "Y"
; type of vertex shaders to use (Hardware/Software/Auto)
; hardware will use whatever the opengl drivers make available
; software will use winex software emulation (will be slow!)
; (has not been implemented yet!)
;; "VertexShaderMode" = "Auto"
"PixelShaders" = "Y"
; Which version of pixel shaders to attempt to use, if available
;;"PixelShadersLevel" = "1.1"
"ClipSpaceFix" = "Y"
; enable software vertex blend weight support (Yes/No/Auto)
; provide software blending fallback if hardware support not available
; (has not been implemented yet!)
;; "SoftwareVertexBlending" = "Auto" 
; (dev-only) Maximum number of texture stages that WineX should attempt to use (1-8)
;; "MaxTextureStages" = "8"
; (dev-only) Identify polygons under the mouse cursor
;; "InterceptMode" = "N"
; (dev-only) apply fragment translation in vertex program (No/Tex/Auto/Pos)
;;"FragmentOffset" = "Auto"
; use the fixed function over vertex shader pipeline (Yes/No/Auto)
;;"FixedProgram" = "Auto"
; (dev-only) Provide non power of two texture support using rectangle textures (Yes/No/Auto)
;;"RectangleTextures" = "Auto"

[opengl]
; Report a truncated list of OpenGL extensions to the application
;;"FixedGLExtensionBuffer" = "N"
; list of additions (+) or deletions (-) to the list of extensions
; reported when FixedGLExtensionBuffer is enabled. Note that extensions
; cannot be enabled if they are not supported by your video card/drivers
;;"GLExtensionBuffer" = "+GL_ARB_imaging,-GL_ARB_depth_texture"

[dinput]
; dead zone for joystick input from 0 to 10000. 1000 is 10% of range.
"DefaultDeadZone" = "1000"

[joystick]
;; Configuration of the function of joystick axes
;; The joystick name and axis functions can be determined with jstest.
;; The available axis types are:
;;   "none", "X", "Y", "Z", "RX", "RY", "RZ",
;;   "slider", "hat", "POV", and "ball"
;; "hat" and "POV" are synonymous. Hats use two axes.

"Logitech Inc. WingMan RumblePad" = "X,Y,slider,Z,RZ,hat,none"

[fonts]
;Read documentation/fonts before adding aliases
"Resolution" = "96"
"Default" = "-adobe-times-"
; Use new improved fonts (uses FreeType and XRender libraries) at user request.
; Defaults to "Y".
;"FreeType" = "N"


[FontPatterns]
"Pattern0" = "-adobe-times*"
"Pattern1" = "-adobe-helvetica*"
"Pattern2" = "-adobe-courier*"
"Pattern3" = "-misc-fixed*"

[FontDirs]
;"0"="/path/to/extra/fonts"

[FontAlias]
;; Add font aliases here. On the left put the name of the windows font family
;; that you want to fake, on the right put the a similar font family that you
;; have installed. These will override the fontconfig and the WineX builtin fallbacks,
;; but may look better (if you choose them correctly).
;; Alias' may refer to other alias' that have been defined above them.
;; These alias' are the first that WineX loads.
;;
;; Serif Fonts
;"Times New Roman"="Times"
"MS Serif"="Times New Roman"
;;
;; Sans Serif Fonts
;"Arial"="Helvetica"
"Helv"="Arial"
"MS Sans Serif"="Arial"
"System"="Arial"
"Tahoma"="Arial"
;;
;; Mono Space Fonts
;"Courier New"="Courier"
;"FixedSys"="Courier"

[memory]
;; Attempt to make memory allocation more windows like.
;; Not for use with all applications. Best used in app default section.
; "MemoryLayoutOverride" = "0x10000000"



[serialports]
"Com1" = "/dev/ttyS0"
"Com2" = "/dev/ttyS1"
"Com3" = "/dev/ttyS2"
"Com4" = "/dev/modem"

[parallelports]
"Lpt1" = "/dev/lp0"

[spooler]
"LPT1:" = "|lpr"
"LPT2:" = "|gs -sDEVICE=bj200 -sOutputFile=/tmp/fred -q -"
"LPT3:" = "/dev/lp3"

[ports]
;"read" = "0x779,0x379,0x280-0x2a0"
; "write" = "0x779,0x379,0x280-0x2a0"

[spy]
"Exclude" = "WM_SIZE;WM_TIMER;"

[registry]
;These are all booleans.  Y/y/T/t/1 are true, N/n/F/f/0 are false.
;Defaults are read all, write to Home
; Global registries (stored in /etc)
"LoadGlobalRegistryFiles" = "n"
; Home registries (stored in ~user/.wine/)
"LoadHomeRegistryFiles" = "Y"
; Load Windows registries from the Windows directory
"LoadWindowsRegistryFiles" = "n"
; TRY to write all changes to home registries
"WritetoHomeRegistryFiles" = "Y"
; Registry periodic save timeout in seconds
; "PeriodicSave" = "600"
; Save only modified keys
"SaveOnlyUpdatedKeys" = "Y"

[Tweak.Layout]
;; supported styles are 'Win31'(default), 'Win95', 'Win98'
"WineLook" = "Win98"

[Console]
"Drivers" = "xterm"
;"Drivers" = "tty"
"XtermProg" = "konsole"
;"InitialRows" = "25"
;"InitialColumns" = "80"
;"TerminalType" = "nxterm"

[Clipboard]
"ClearAllSelections" = "0"
"PersistentSelection" = "1"

; List of all directories directly contain .AFM files
[afmdirs]
;"1" = "/usr/share/ghostscript/fonts"
;"2" = "/usr/share/a2ps/afm"
;"3" = "/usr/share/enscript"
;"4" = "/usr/X11R6/lib/X11/fonts/Type1"

[Wineserver]
"SHMWineserver" = "Y"

[WinMM]
"Drivers" = "wineoss.drv"
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[wineoss]
"UseMMap" = "N"
"FullDuplex" = "N"
;; Specify a mapping for what digital audio devices to use
;"dsp0" = "/dev/dsp0"
;"mixer0" = "/dev/mixer0"

[winealsa]
"UseMMap" = "Y"
;"pcm0" = "hw"
;"ctl0" = "hw"

;; App default settings

;; Battle Field 1942 settings
[AppDefaults\\bf1942.exe\\d3dgl]
"ClipSpaceFix" = "N"

;; Medal Of Honor settings
[AppDefaults\\mohaa.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\mohaa.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"
[AppDefaults\\mohaademo.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\mohaademo.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"

[AppDefaults\\moh_spearhead.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\moh_spearhead.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"
[AppDefaults\\moh_spearhead.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\moh_spearhead_demo.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\moh_spearhead_demo.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"

[AppDefaults\\moh_breakthrough.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"
[AppDefaults\\moh_breakthrough.exe\\version]
"windows" = "win2k"

;; SimCity 4 settings
[AppDefaults\\SimCity 4.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\SimCity 4.exe\\transgaming]
"cmdlineadd" = "-d:software"

;; Civ 3
[AppDefaults\\Civilization3.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\Civilization3x.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\civ3conquests.exe\\Version]
"Windows" = "win2k"

;; Call of Duty
[AppDefaults\\CoDSP.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\CoDMP.exe\\Version]
"Windows" = "win2k"

;; City of Heros
[AppDefaults\\CityOfHeroes.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\CityOfHeroes.exe\\cursor]
"CursorAlphaAlwaysOn" = "Y"
[AppDefaults\\CohUpdater.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\CohUpdater.exe\\cursor]
"CursorAlphaAlwaysOn" = "Y"

;; Command & Conquer: Generals
[AppDefaults\\Generals.exe\\Version]
"Windows" = "win2k"

;; Painkiller
[AppDefaults\\Painkiller.exe\\Version]
"Windows" = "win2k"

;; EverQuest
[AppDefaults\\eqgame.exe\\d3dgl]
"ClipSpaceFix" = "N"
"ForceMaxVertexBlendMatrices" = "2" 
[AppDefaults\\testeqgame.exe\\d3dgl]
"ClipSpaceFix" = "N"
"ForceMaxVertexBlendMatrices" = "2" 

;; Half-life 2
[AppDefaults\\hl2.exe\\d3dgl]
"ForceMaxVertexBlendMatrices" = "2" 

;; Need for Speed Underground
[AppDefaults\\Speed.exe\\d3dgl]
"PixelShaders" = "N"

;; Max Payne 2
[AppDefaults\\MaxPayne2.exe\\d3dgl]
"PixelShaders" = "N"

;; Doom 3
[AppDefaults\\Doom3.exe\\Version]
"Windows" = "win2k"

;; Far Cry
[AppDefaults\\FarCry.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\FarCry.exe\\d3dgl]
"PretendGeforceTwoForFixedFunction" = "Y"

;; Sid Meier's Pirates!
[AppDefaults\\Pirates\!.exe\\d3dgl]
"ForceMaxTextureBlendStages" = "8"
# </wineconf>

---

### Post by NateC on 2005-04-09
any ideas?

---

### Post by telmo on 2005-04-09
This one (game!) is just killing me! I want sooo much to format my windows partition... but i can't lose Counter Strike!!! Nooooo way!

---

### Post by NateC on 2005-04-10
Telmo check out this thread, it worked for me. 

[http://ubuntuforums.org/showthread.php?p=123607#post123607](http://ubuntuforums.org/showthread.php?p=123607#post123607)

---

### Post by telmo on 2005-04-10
Thank you! I'll try it A.S.A.P.

---

