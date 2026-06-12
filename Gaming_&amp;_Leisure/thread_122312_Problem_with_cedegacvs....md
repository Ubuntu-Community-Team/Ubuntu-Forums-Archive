---
title: "Problem with cedegacvs..."
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by Sordo on 2006-01-27
I installed cvscedega using profile : "cvscedega_head" and got it installed.
But when i try to type:[INDENT]mika@ubuntu:~/Desktop$ cvscedega
  
cvscedega Features:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:    cvscedega regapi <regfilename.reg>
Install .reg with regedit:   cvscedega regedit [regfilename.reg]
Install a .dll with regedit: cvscedega regsvr32 [filename.dll]
Start winecfg:               cvscedega winecfg
Log to file:                 cvscedega log <normal params>
         eg:                 cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console
  
Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/mika/.cvscedega/config'
mika@ubuntu:~/Desktop$
  
[/INDENT]I got this, Then i try to run 
[INDENT]mika@ubuntu:~/games/World of Warcraft$ cvscedega WoW.exe
Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/mika/.cvscedega/config'
mika@ubuntu:~/games/World of Warcraft$
  
[/INDENT]And got that. I installed cvscedega with [INDENT][http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45")
  
[/INDENT]With that tutorial. But I don't know do I configure config-file correctly.

I paste my config-file here:
[INDENT]WINE REGISTRY Version 2
;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config
  
;; If you think it is nescessary to show others your complete config for a 
;; bug report, filter out empty lines and comments with
;; grep -v "^;" ~/.wine/config | grep '.' 
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
"Path" = "/home/mika/windows/C"
"Type" = "hd"
"Label" = "Dos Drive"
"Filesystem" = "win95"
 
[Drive D]
"Path" = "/cdrom"
"Type" = "cdrom"
"Label" = "CD-ROM"
"Filesystem" = "win95"
"Device" = "/dev/hdc" 
 
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
;"ShowDirSymlinks" = "1"
; Note: The WINESHELLLINK Environment variable will override this setting.
;       (which is set in the winex startup script)
"ShellLinker" = "/usr/lib/transgaming/winex/bin/wineshelllink"
; Note: The WINEBROWSER Environment variable will override this setting.
;       you may format the string by placing a %s where you want
;       the URL to go, if its left off then the URL will be appended to the end.
; This option is used by the winelib app 'winebrowserlink'
"Browser" = "/usr/bin/mozilla %s"
  
# <wineconf>
  
[Version]
; This doesn't work in WineX, but its here for WineHQ compatability.
; can be (win95, win98, winme, nt351, nt40, win2k, winxp, win20, win30, win31)
"Windows" = "win98"
; dos version
;"DOS" = "6.22"
  
[DllDefaults]
"DefaultLoadOrder" = "native, builtin, so"
  
[DllOverrides]
"commdlg"      = "builtin, native"
"comdlg32"     = "builtin, native"
"ver"          = "builtin, native"
"version"      = "builtin, native"
"shell"        = "builtin, native"
"shell32"      = "builtin, native"
"shfolder"     = "builtin, native"
"shlwapi"      = "builtin, native"
"shdocvw"      = "builtin, native"
"lzexpand"     = "builtin, native"
"lz32"         = "builtin, native"
"comctl32"     = "builtin, native"
"commctrl"     = "builtin, native"
"advapi32"     = "builtin, native"
"crtdll"       = "builtin, native"
"mpr"          = "builtin, native"
"winspool.drv" = "builtin, native"
"d3d8"         = "builtin, native"
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
  
[x11drv]
; How much Video RAM does your graphic card have?
; If this option is not present, it will default set to 32MB.
"VideoRam" = "128"
; How much should Cedega attempt to store into faster AGP memory
; Set the amount of video memory to be allocated for OpenGL vertex arrays.
"AGPVertexRam" = "32"
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
; Use a desktop window of 640x480 for Wine
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
  
  
[fonts]
;Read documentation/fonts before adding aliases
"Resolution" = "96"
"Default" = "-adobe-times-"
"Freetype" = "Y"
  
[FontPatterns]
"Pattern0" = "-adobe-times*"
"Pattern1" = "-adobe-helvetica*"
"Pattern2" = "-adobe-courier*"
"Pattern3" = "-misc-fixed*"
                                
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
  
[WinMM]
"Drivers" = "wineoss.drv"
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"
  
[wineoss]
"UseMMap" = "Y"
"FullDuplex" = "N"
  
;; sample AppDefaults entries
;[AppDefaults\\iexplore.exe\\DllOverrides]
;"shlwapi" = "native"
;"rpcrt4" = "native"
;"ole32" = "native"
;"shdocvw" = "native"
;"wininet" = "native"
;"shfolder" = "native"
;"shell32" = "native"
;"shell" = "native"
;"comctl32" = "native"
;
;[AppDefaults\\setup.exe\\x11drv]
;"Desktop" = "800x600"
  
# </wineconf>
  
[/INDENT]When tutorial said that:[INDENT]   ; How much Video RAM does your graphic card have?
; If this option is not present, it will default set to 32MB.
"VideoRam" = "128"
; How much should Cedega attempt to store into faster AGP memory
; Set the amount of video memory to be allocated for OpenGL vertex arrays.
"AGPVertexRam" = "32"
[/INDENT]I didn't find those rows from config-file and so added those myself...
Please help me :/

---

### Post by princedwi on 2006-01-28
At the moment i'm trying to install CedegaCVS on my main. On my laptop, I got up to your point right now. 

What you're looking for is located in the "[x11drv]" section. It's located right in between the "[DllOverrides]" and the "[fonts]" brackets.

Right now my only issue is the fact that when I run "cedegacvs" on the terminal, it claims it's not a command...so bleh. Other than that, I should've been fine. I hope this helps!

---

### Post by handy on 2006-01-29
I know next to nothing about this, but I have put together cvscedega a couple of weeks ago, & It gives no errors.

You won't get any sense out of typing cvscedega into the terminal.  

I installed Guild Wars in the following path:

**/home/<user name>/.cvscedega/drive_c/Program  Files/Guild Wars/**

To run GW I used nautilus, **Menu:** ***View/Show Hidden Files***  Then followed the above path to the GW directory, double click on GW.exe & it runs up as far as the GW login screen, where I can hear the music, & use my mouse & login, then black screen of death! :confused: 

I made a link from the right mouse button menu, to the GW.exe file, & moved the new icon to my desktop, so that I can far more conveniently test, after editing the cvscedega config file.

I am looking for help too, I have posted a new thread re: GW & cvscedega, & also asking which is the fastest of the cedega versions specifically for running GW.

I may have to buy a short subscription, to be able to play GW on Ubuntu, instead of doing it from xp, where of course it functions perfectly, for the obvious reasons!

---

