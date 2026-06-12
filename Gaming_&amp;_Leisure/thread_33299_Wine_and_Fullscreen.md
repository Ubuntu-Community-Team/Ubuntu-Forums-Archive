---
title: "Wine and Fullscreen"
date: 2005-05-10
forum: Gaming &amp; Leisure
---

### Post by globalspace on 2005-05-10
hi all,
i have a problem with wine :
every time that i start a game in fullscreen mode i have a lot of different error , for example Diablo II says me :
> Error 22 : A critical error has occoured while initializing Direct Draw 
and Abe's Exoddus says me :
> Can't set mode : trying 640x480x8 
i click Ok and then :
> Can't set mode : trying 640x480x16 
i re-click Ok and then :
> SetMode Failed err= 200532552 

it seems like wine's game can't set the resolution ... 

so if I want to play i must Decomment this line :

> 
; Use a desktop window of 640x480 for Wine
"Desktop" = "1280x1024" 

but wine start into a small window (i think 640x480) ...

this is my .wine/conf :

> WINE REGISTRY Version 2
;;All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;; If you think it is necessary to show others your complete config for a
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
;;   - "win95" for ext2fs, VFAT and FAT3
;;   - "msdos" for FAT16 (ugly, upgrading to VFAT driver strongly recommended)
;;   DON'T use "unix" unless you intend to port programs using Winelib !
;; "Device"="/dev/xx" (only if you want to allow raw device access)
;;

[Drive A]
"Path" = "/media/floppy0"
"Type" = "floppy"
"Label" = "Floppy"
"Device" = "/dev/fd0"

[Drive C]
"Path" = "/home/massi/.wine/fake_windows"
"Type" = "hd"
"Label" = "/home/massi/.wine/fake_windows"
"Filesystem" = "win95"

[Drive D]
"Path" = "/mnt/fat32"
"Type" = "hd"
"Label" = "/mnt/fat32"
"Filesystem" = "win95"

[Drive E]
"Path" = "/media/cdrom1"
"Type" = "cdrom"
"Label" = "/media/cdrom1"
"Filesystem" = "win95"
"Device" = "/dev/hdc"

[Drive F]
"Path" = "/media/cdrom0"
"Type" = "cdrom"
"Label" = "/media/cdrom0"
"Filesystem" = "win95"
"Device" = "/dev/hdd"

[Drive X]
"Path" = "/tmp"
"Type" = "hd"
"Label" = "Tmp Drive"
"Filesystem" = "win95"

[Drive Y]
"Path" = "%HOME%"
"Type" = "network"
"Label" = "Home"
"Filesystem" = "win95"

[Drive Z]
"Path" = "/"
"Type" = "hd"
"Label" = "Root"
"Filesystem" = "win95"

[wine]
"Windows" = "C:\\Windows"
"System" = "C:\\Windows\\System"
"Temp" = "X:\\"
"Path" = "C:\\Windows;C:\\Windows\\System;X:\\;X:\\test;Y:\\"
"GraphicsDriver" = "x11drv"
; Wine doesn't pass directory symlinks to Windows programs by default.
; Enabling this may crash some programs that do recursive lookups of a whole
; subdir tree in case of a symlink pointing back to itself.
;"ShowDirSymlinks" = "1"
;"ShowDotFiles" = "1"
"ShellLinker" = "wineshelllink"

# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
"Windows" = "winxp"
; DOS version to imitate
;"DOS" = "6.22"

; Be careful here, wrong DllOverrides settings have the potential
; to pretty much kill your setup.

[DllOverrides]
; some dlls you may want to change
"oleaut32" = "builtin, native"
"ole32" = "builtin, native"
"commdlg" = "builtin, native"
"comdlg32" = "builtin, native"
"shell" = "builtin, native"
"shell32" = "builtin, native"
"shfolder" = "builtin, native"
"shlwapi" = "builtin, native"
"shdocvw" = "builtin, native"
"advapi32" = "builtin, native"
"msvcrt" = "native, builtin"
"mciavi.drv" = "native, builtin"
"mcianim.drv" = "native, builtin"
"msi" = "native, builtin"
; you can specify applications too
; this one will apply for all notepad.exe
;"*notepad.exe" = "native, builtin"
; this one will apply only for a particular file
;"C:\\windows\\regedit.exe" = "native, builtin"
; default for all other dlls
"*" = "builtin, native"

[x11drv]
; Number of colors to allocate from the system palette
"AllocSystemColors" = "100"
; Use a private color map
"PrivateColorMap" = "N"
; Favor correctness over speed in some graphics operations
"PerfectGraphics" = "N"
; Color depth to use on multi-depth screens
"ScreenDepth" = "32"
; Name of X11 display to use
;;"Display" = ":0.0"
; Allow the window manager to manage created windows
;"Managed" = "Y"
; Use a desktop window of 640x480 for Wine
;"Desktop" = "1280x1024"
; Use XFree86 DGA extension if present
; (make sure /dev/mem is accessible by you !)
"UseDGA" = "Y"
; Use XVidMode extension if present
"UseXVidMode" = "Y"
; Use XRandR extension if present
"UseXRandR" = "Y"
; Use the take focus protocol
"UseTakeFocus" = "Y"
; Enable DirectX mouse grab
"DXGrab" = "N"
; Create the desktop window with a double-buffered visual
; (useful to play OpenGL games)
"DesktopDoubleBuffered" = "Y"
; Run in synchronous mode (useful for debugging X11 problems)
;;"Synchronous" = "Y"
;
; Use the Render extension to render client side fonts (default "Y")
;;"ClientSideWithRender" = "Y"
; Fallback on X core requests to render client side fonts (default "Y")
;;"ClientSideWithCore" = "Y"
; Set both of the previous two to "N" in order to force X11 server side fonts
;
; Anti-alias fonts if using the Render extension (default "Y")
;;"ClientSideAntiAliasWithRender" = "Y"
; Anti-alias fonts if using core requests fallback (default "Y")
;;"ClientSideAntiAliasWithCore" = "Y"
;

[fonts]
;Read the Fonts topic in the Wine User Guide before adding aliases
;See a couple of examples for russian users below
"Resolution" = "96"
"Default" = "-adobe-helvetica-"
"DefaultFixed" = "fixed"
"DefaultSerif" = "-adobe-times-"
"DefaultSansSerif" = "-adobe-helvetica-"

;; default TrueType fonts with russian koi8-r encoding
;"Default" = "-monotype-arial-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultFixed" = "-monotype-courier new-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultSerif" = "-monotype-times new roman-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultSansSerif" = "-monotype-arial-*-*-*--*-*-*-*-*-*-koi8-r"
;; default cyrillic bitmap X fonts
;"Default" = "-cronyx-helvetica-"
;"DefaultFixed" = "fixed"
;"DefaultSerif" = "-cronyx-times-"
;"DefaultSansSerif" = "-cronyx-helvetica-"

; the TrueType font dirs you want to make accessible to wine

[FontDirs]
;"dir1" = "/usr/X11R6/lib/X11/fonts/TrueType"
;"dir2" = "/usr/share/fonts/truetype"
;"dir3" = "/usr/X11R6/lib/X11/fonts/TT"
;"dir4" = "/usr/share/fonts/TT"

[serialports]
"Com1" = "/dev/ttyS0"
"Com2" = "/dev/ttyS1"
"Com3" = "/dev/ttyS2"
"Com4" = "/dev/modem"

[parallelports]
"Lpt1" = "/dev/lp0"

[ppdev]
;; key:  io-base of the emulated port
;; value : parport-device{,timeout}
;; timeout for auto closing an open device ( not yet implemented)
;"378" = "/dev/parport0"
;"278" = "/dev/parport1"
;"3bc" = "/dev/parport2"

[spooler]
"FILE:" = "tmp.ps"
"LPT1:" = "|lpr"
"LPT2:" = "|gs -sDEVICE=bj200 -sOutputFile=/tmp/fred -q -"
"LPT3:" = "/dev/lp3"

[ports]
;"read" = "0x779,0x379,0x280-0x2a0"
;"write" = "0x779,0x379,0x280-0x2a0"

[Debug]
;"RelayExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"RelayInclude" = "user32.CreateWindowA"
;"RelayFromExclude" = "user32;x11drv"
;"RelayFromInclude" = "sol.exe"
;"SnoopExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"SpyExclude" = "WM_SIZE;WM_TIMER;"

[registry]
;These are all booleans.  Y/y/T/t/1 are true, N/n/F/f/0 are false.
;Defaults are read all, write to Home
; Where to find the global registries
;"GlobalRegistryDir" = "/etc";
; Global registries (stored in /etc)
"LoadGlobalRegistryFiles" = "Y"
; Home registries (stored in ~user/.wine/)
"LoadHomeRegistryFiles" = "Y"
; Load Windows registries from the Windows directory
"LoadWindowsRegistryFiles" = "Y"
; TRY to write all changes to home registries
"WritetoHomeRegistryFiles" = "Y"
; Registry periodic save timeout in seconds
; "PeriodicSave" = "600"
; Save only modified keys
"SaveOnlyUpdatedKeys" = "Y"

[Tweak.Layout]
;; supported styles are 'Win31'(default), 'Win95', 'Win98'
;; this has *nothing* to do with the windows version Wine returns:
;; set the "Windows" value in the [Version] section if you want that.
"WineLook" = "Win98"

[Clipboard]
"ClearAllSelections" = "0"
"PersistentSelection" = "1"

; List of all directories directly contain .AFM files

[afmdirs]
"1" = "/usr/share/ghostscript/fonts"
"2" = "/usr/share/a2ps/afm"
"3" = "/usr/share/enscript"
"4" = "/usr/X11R6/lib/X11/fonts/Type1"

[WinMM]
; Uncomment the "Drivers" line matching your sound setting.

"Drivers" = "wineoss.drv"      ; default for most common configurations
;"Drivers" = "winearts.drv"    ; for KDE
;"Drivers" = "winealsa.drv"    ; for ALSA users
;"Drivers" = "winejack.drv"    ; for Jack sound server
;"Drivers" = "winenas.drv"     ; for NAS sound system
;"Drivers" = "wineaudioio.drv" ; for Solaris machines
;"Drivers" = ""                ; to disable sound
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.NO
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)
"HardwareAcceleration" = "Emulation"
;; Sets default playback device (0 - number of devices - 1)
"DefaultPlayback" = "0"	; use first device (/dev/dsp)
;"DefaultPlayback" = "1" 	; use second device (/dev/dsp1)
;"DefaultPlayback" = "2" 	; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)
;"DefaultCapture" = "0"		; use first device (/dev/dsp)
;"DefaultCapture" = "1"		; use second device (/dev/dsp1)
;"DefaultCapture" = "2"		; use third device (/dev/dsp2)

[Network]
;; Use the DNS (Unix) host name always as NetBIOS "ComputerName" (boolean, default "Y").
;; Set to N if you need a persistent NetBIOS ComputerName that possibly differs 
;; from the Unix host name. You'll need to set ComputerName in 
;; HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ComputerName\ComputerName, too.
;"UseDnsComputerName" = "N"

#########################################
# Application dependent sections follow #
#########################################

[AppDefaults\\_INS5576._MP\\x11drv]
; Lotus Notes R5 installer
; I'm quite not sure this will run on some other machine than mine, but it 
; can't hurt
"Managed" = "N"
"Desktop" = "N"

[AppDefaults\\nlnotes.exe\\x11drv]
"Desktop" = "800x600"

[AppDefaults\\explorer.exe\\x11drv]
"Desktop" = "800x600"

[AppDefaults\\notes.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

[AppDefaults\\nlnotes.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

[AppDefaults\\nhldaemn.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

# [/wineconf]



---

### Post by max0000 on 2005-07-03
Try set:

; Use XRandR extension if present
"UseXRandR" = "Y"

and NO desktop window for wine:

;Use a desktop window of 640x480 for Wine
;"Desktop" = "1280x1024"

Work for me.

---

