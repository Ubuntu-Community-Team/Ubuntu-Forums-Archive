---
title: "Hi, New kubuntu installation"
date: 2006-09-16
forum: Desktop Environments
---

### Post by ScarFreewill on 2006-09-16
I got some probs with kubuntu6.06(x86):

GFX:
Firstly I installed nvidia-glx and its deps via adept, made a backup of the xorg.conf and did 'sudo nvidia-glx-config enable' then it told me my xorg.conf was edited and it can't change it (i'm guessing kubuntu detected my screen or something and now it saved it in my xorg.conf), so I just change nv to nvidia but leave this the same 
> Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
Then I added the Option "NoLogo" under Section "Device". Now I have direct rendering or whaterver u call it glxgears is runing and glxinfo says vendor nvidia...

OTHER:
I realy dislike it that it wants to set my time to gtm2+ if my pc clock is already set to it, so i have to say i live in Reykjavik lol and my keyboard is being detected weardly is just got a normal keyboard, but if I press (&#8220;) i get (@) and with (hash) i get (£) some of my buttons are mixed around which sucks and some of them i can't write like hash which realy sucks.

WINE:
I want to compile wine from source. I installed gcc-4.0 when I compile wine it does not detect gcc and in my console if I tipe gcc it says 'bash: gcc: command not found' but if I tipe gcc-4.0 then it says 'gcc-4.0: no input files' so I have it, but it just is not set to gcc?

ps: I found hash its instead of 'back-slash' but now i can't make a back-slash this is realy crap and boson crashes every time before i can get into the actual game (I can get into the menu)

---

### Post by ScarFreewill on 2006-09-16
This is what the console said:

```

freewill@freewill-desktop:~$ boson
[int main(int, char**)] resolving GL, GLX and GLU symbols
libGL.so: cannot open shared object file: No such file or directory
WARNING: [QLibrary* loadLibrary(const QString&)] library GL could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
searching in dir /lib
searching in dir /usr/lib
using file /usr/lib/libGL.so.1
libGLU.so: cannot open shared object file: No such file or directory
WARNING: [QLibrary* loadLibrary(const QString&)] library GLU could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
searching in dir /lib
searching in dir /usr/lib
using file /usr/lib/libGLU.so.1
[int main(int, char**)] GL, GLX and GLU symbols successfully resolved
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libGL.so: cannot open shared object file: No such file or directory
boson: WARNING: [QLibrary* loadLibrary(const QString&)] library GL could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
libGLU.so: cannot open shared object file: No such file or directory
boson: WARNING: [QLibrary* loadLibrary(const QString&)] library GLU could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
boson: WARNING: [bool BoPluginManager::makePluginCurrent(const QString&)] boConfig requested plugin BosonGameViewDefault but it was not available
boson: WARNING: [bool BoUfoXMLBuilder::mergeMenuBars(QDomElement&, QDomElement&)] custom menus/toplevel items ignore MergeLocal tags
boson: WARNING: [bool BoUfoXMLBuilder::mergeMenuBars(QDomElement&, QDomElement&)] custom menus/toplevel items ignore MergeLocal tags
boson: WARNING: [bool BoUfoXMLBuilder::mergeMenuBars(QDomElement&, QDomElement&)] custom menus/toplevel items ignore MergeLocal tags
boson: WARNING: [bool BoUfoXMLBuilder::mergeMenuBars(QDomElement&, QDomElement&)] custom menus/toplevel items ignore MergeLocal tags
boson: WARNING: [bool BosonPlayField::loadFromDiskToFiles(QMap<QString, QMemArray<char> >&)] NULL file - recreating file pointer
Could not open vorbisfile library: libvorbisfile.so: cannot open shared object file: No such file or directory
Boson Sound: ERROR: [bool BosonAudioAL::loadFileToBuffer(ALuint, const QString&)] alutLoadVorbis_LOKI failed for file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: ERROR: [void BoPlayObject::reload()] unable to load file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: WARNING: [virtual void BosonSound::addEventSound(const QString&, const QString&)] NULL sound /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg for order_move
KCrash: Application 'boson' crashing...
alsa_blitbuffer: Could not write audio data to sound device: Input/output error
ALSA lib pcm_direct.c:1136:(snd_pcm_direct_set_timer_params) unable to set timer parameters
freewill@freewill-desktop:~$  

```

---

