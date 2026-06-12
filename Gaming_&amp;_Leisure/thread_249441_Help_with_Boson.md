---
title: "Help with Boson"
date: 2006-09-02
forum: Gaming &amp; Leisure
---

### Post by Xzallion on 2006-09-02
I installed Boson from the repositories, and I can't seem to run it.  Heres the output from a terminal, can someone help me figure this out?
```

kenneth@Xzallion-Ubuntu:~$ boson
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
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libGL.so: cannot open shared object file: No such file or directory
boson: WARNING: [QLibrary* loadLibrary(const QString&)] library GL could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
libGLU.so: cannot open shared object file: No such file or directory
boson: WARNING: [QLibrary* loadLibrary(const QString&)] library GLU could not be loaded using standard QLibrary/dlopen(). Trying to guess correct filename
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
KCrash cannot reach kdeinit, launching directly.
kenneth@Xzallion-Ubuntu:~$

```

---

### Post by Perfect Storm on 2006-09-02
wow...doesn't look good.

Well...I guess you have installed 3D acc. driver for your card? It also complain about libglu, is it installed?

Also look that there's some trouble with the soundcard.

---

### Post by Ariccanfly on 2008-03-08
Boson Sound: [bool BosonAudioAL::loadFileToBuffer(ALuint, const QString&)] loading ogg vorbis file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Could not open vorbisfile library: libvorbisfile.so: cannot open shared object file: No such file or directory
Boson Sound: ERROR: [bool BosonAudioAL::loadFileToBuffer(ALuint, const QString&)] alutLoadVorbis_LOKI failed for file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: ERROR: [void BoPlayObject::reload()] unable to load file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: [virtual void BosonSound::addEventSound(const QString&, const QString&)] loading /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: WARNING: [virtual void BosonSound::addEventSound(const QString&, const QString&)] NULL sound /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg for order_move
Boson Sound: [void BoPlayObject::reload()] /usr/share/apps/boson/themes/species/human/sounds/order_move_1.ogg
Boson Sound: [bool BosonAudioAL::loadFileToBuffer(ALuint, const QString&)] loading ogg vorbis file /usr/share/apps/boson/themes/species/human/sounds/order_move_1.ogg
emergencySave(): retrieving current time for filenames
emergencySave(): trying to save game logs
boson: [bool BoGameLogSaver::saveMessageLog()] message log saved to boson_crash-20080307235835.messagelog
boson: [bool Boson::saveGameLogs(const QString&)] Done, elapsed: 73709
emergencySave(): game logs saved
alsa_blitbuffer: Could not write audio data to sound device: Input/output error
ALSA lib pcm_direct.c:1268:(snd_pcm_direct_set_timer_params) unable to set timer parameters
KCrash: Application 'boson' crashing...

is my crash... ??

---

