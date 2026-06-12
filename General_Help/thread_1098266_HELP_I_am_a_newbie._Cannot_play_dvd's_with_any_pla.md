---
title: "HELP I am a newbie. Cannot play dvd's with any player."
date: 2009-03-16
forum: General Help
---

### Post by dstanfel on 2009-03-16
Hello all. I need some serious help.  I have Ubuntu 8.10 and I am a newbie. I have worked for the last 3 days installing and trying the different media players to be able to play store bought DVDs and I cannot get anything to work. I finally got sound on two of the movie players but nothing else. I have been through all of the forums and followed the installations step by step and still nothing. if someone could walk me through either VLC or mplayer and help me get it working I would greatly appreciate it.

---

### Post by taurus on 2009-03-16
Did you install libdvdcss2?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dstanfel on 2009-03-17
I have installed everything I could find to install. I have followed the instructions on medibuntu. I have tried to install mplayer, smplayer, vcl, xine,kmplayer. basically you name it I have found it, installed it following the directions via cut and paste and the most I get is sound, no video. I have installed libraries, codecs, keys and now I dont know where to turn.  I am completely lost. I have even tried to uninstall and reinstall each media player at least 3 times. So if someone can help me by walking me through an uninstall and install of vcl or mplayer and everything I need for each one to be able to play store bought dvd's I would appreciate it.

---

### Post by rvm4000 on 2009-03-17
It would helpful to know the output (log) of the players.

In smplayer, select *Options -> View logs -> mplayer* _after_ trying to play a dvd, and copy the log here.

---

### Post by dstanfel on 2009-03-17
here is the log for smplayer.
[11:36:51] main: lock_file: /home/mom/.config/smplayer/smplayer_init.lock
[11:36:51] global_init
[11:36:51] global_init: config file: '/home/mom/.config/smplayer/smplayer.ini'
[11:36:51] Preferences::load
[11:36:51] AssStyles::load
[11:36:51] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
[11:36:51] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
[11:36:51] Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
[11:36:51] This is SMPlayer v. 0.6.7 (SVN r2831) running on Linux
[11:36:51] Compiled with Qt v. 4.3.4, using 4.4.3
[11:36:51]  * application path: '/usr/bin'
[11:36:51]  * data path: '/usr/share/smplayer'
[11:36:51]  * translation path: '/usr/share/smplayer/translations'
[11:36:51]  * doc path: '/usr/share/doc/smplayer'
[11:36:51]  * themes path: '/usr/share/smplayer/themes'
[11:36:51]  * shortcuts path: '/usr/share/smplayer/shortcuts'
[11:36:51]  * config path: '/home/mom/.config/smplayer'
[11:36:51]  * ini path: '/home/mom/.config/smplayer'
[11:36:51]  * file for subtitles' styles: '/home/mom/.config/smplayer/styles.***'
[11:36:51]  * current path: '/home/mom'
[11:36:51] SMPlayer::processArgs: arguments: 1
[11:36:51] SMPlayer::processArgs: 0 = smplayer
[11:36:51] SMPlayer::processArgs: files_to_play: count: 0
[11:36:51] MyClient::MyClient
[11:36:51] SMPlayer::processArgs: trying to connect to port 47019
[11:36:51] SMPlayer::gui: changed working directory to app path
[11:36:51] SMPlayer::gui: current directory: /usr/bin
[11:36:51] Core::changeFileSettingsMethod: hash
[11:36:51] MplayerLayer::setRepaintBackground: 0
[11:36:51] Preferences::monitor_aspect_double
[11:36:51]  warning: monitor_aspect couldn't be parsed!
[11:36:51]  monitor_aspect set to 0
[11:36:52] Playlist::setModified: 0
[11:36:52] Playlist::loadSettings
[11:36:52] Playlist::addItem: 'dvd://1//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://2//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://3//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://4//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://5//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://6//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://7//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://8//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://9//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://10//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://11//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://12//dev/dvd'
[11:36:52] Playlist::addItem: 'dvd://13//dev/dvd'
[11:36:52] Playlist::setModified: 0
[11:36:52] Playlist::updateView
[11:36:52] Playlist::updateView: name: 'dvd://1//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://2//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://3//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://4//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://5//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://6//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://7//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://8//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://9//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://10//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://11//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://12//dev/dvd'
[11:36:52] Playlist::updateView: name: 'dvd://13//dev/dvd'
[11:36:52] Style name: 'cleanlooks'
[11:36:52] Style class name: 'QCleanlooksStyle'
[11:36:52] BaseGui::initializeMenus
[11:36:52] BaseGui::initializeMenus
[11:36:52] BaseGui::updateRecents
[11:36:52] BaseGui::updateWidgets
[11:36:52] Core::changeUseAss: 1
[11:36:52] BaseGui::setStayOnTop: 0
[11:36:52] BaseGui::setStayOnTop: nothing to do
[11:36:52] BaseGui::updateWidgets
[11:36:52] BaseGui::updateWidgets
[11:36:52] BaseGui::updateRecents
[11:36:52] Preferences::save
[11:36:52] AssStyles::save
[11:36:52] BaseGui::initializeGui: server running on port 43184
[11:36:52] BaseGui::initializeMenus
[11:36:52] BaseGui::updateRecents
[11:36:52] BaseGui::updateWidgets
[11:36:52] BaseGuiPlus::loadConfig
[11:36:52] DefaultGui::createStatusBar
[11:36:52] DefaultGui::createActions
[11:36:52] DefaultGui::createControlWidget
[11:36:52] DefaultGui::createControlWidgetMini
[11:36:52] BaseGui::initializeMenus
[11:36:52] BaseGui::updateRecents
[11:36:52] DefaultGui::updateWidgets
[11:36:52] BaseGui::updateWidgets
[11:36:52] DefaultGui::loadConfig
[11:36:52] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1440 h:900
[11:36:52] ToolbarEditor::load: 'toolbar1'
[11:36:52] ToolbarEditor::load: loading action open_file
[11:36:52] ToolbarEditor::load: loading action open_dvd
[11:36:52] ToolbarEditor::load: loading action open_url
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action compact
[11:36:52] ToolbarEditor::load: loading action fullscreen
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action screenshot
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action show_file_properties
[11:36:52] ToolbarEditor::load: loading action show_playlist
[11:36:52] ToolbarEditor::load: loading action show_preferences
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action play_prev
[11:36:52] ToolbarEditor::load: loading action play_next
[11:36:52] ToolbarEditor::load: 'controlwidget'
[11:36:52] ToolbarEditor::load: loading action play
[11:36:52] ToolbarEditor::load: loading action pause_and_frame_step
[11:36:52] ToolbarEditor::load: loading action stop
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action rewindbutton_action
[11:36:52] ToolbarEditor::load: loading action timeslider_action
[11:36:52] TimeSlider::setDragDelay: 100
[11:36:52] ToolbarEditor::load: loading action forwardbutton_action
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action fullscreen
[11:36:52] ToolbarEditor::load: loading action mute
[11:36:52] ToolbarEditor::load: loading action volumeslider_action
[11:36:52] ToolbarEditor::load: 'controlwidget_mini'
[11:36:52] ToolbarEditor::load: loading action play_or_pause
[11:36:52] ToolbarEditor::load: loading action stop
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action rewind1
[11:36:52] ToolbarEditor::load: loading action timeslider_action
[11:36:52] TimeSlider::setDragDelay: 100
[11:36:52] ToolbarEditor::load: loading action forward1
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action mute
[11:36:52] ToolbarEditor::load: loading action volumeslider_action
[11:36:52] ToolbarEditor::load: ''
[11:36:52] ToolbarEditor::load: loading action play
[11:36:52] ToolbarEditor::load: loading action pause
[11:36:52] ToolbarEditor::load: loading action stop
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action rewindbutton_action
[11:36:52] ToolbarEditor::load: loading action timeslider_action
[11:36:52] TimeSlider::setDragDelay: 100
[11:36:52] ToolbarEditor::load: loading action forwardbutton_action
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action fullscreen
[11:36:52] ToolbarEditor::load: loading action mute
[11:36:52] ToolbarEditor::load: loading action volumeslider_action
[11:36:52] ToolbarEditor::load: loading action separator
[11:36:52] ToolbarEditor::load: adding separator
[11:36:52] ToolbarEditor::load: loading action timelabel_action
[11:36:52] Helper::qtVersion: 4403
[11:36:52] DefaultGui::loadConfig: playlist visible: 0
[11:36:52] DefaultGui::loadConfig: playlist position: 23, 23
[11:36:52] DefaultGui::loadConfig: playlist size: 720 x 360
[11:36:52] DefaultGui::updateWidgets
[11:36:52] BaseGui::updateWidgets
[11:36:52] BaseGui::showEvent
[11:36:52] main: remove_lock: /home/mom/.config/smplayer/smplayer_init.lock
[11:36:52] BaseGui::loadActions
[11:36:52] ActionsEditor::loadFromConfig
[11:36:53] BaseGui::initializeMenus
[11:36:53] BaseGui::updateRecents
[11:36:53] DefaultGui::updateWidgets
[11:36:53] BaseGui::updateWidgets
[11:37:04] BaseGui::showLog

---

### Post by dstanfel on 2009-03-17
I have no options on mplayer to be able to get the logs.

---

### Post by rvm4000 on 2009-03-17
> **dstanfel said:**
> here is the log for smplayer.

It seems you copied the log before trying to play a dvd, so it doesn't contain any information regarding to dvd playback.

Options -> View logs -> MPlayer **after** trying to play a dvd. (if the log is empty, be sure the option "Log mplayer output" in Preferences->Advanced->Logs is enabled)

Or open a terminal, run this, and copy the output:
```
mplayer dvd://
```

---

### Post by dstanfel on 2009-03-17
mom@mom-laptop:~$ mplayer dvd://
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T1300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 13 titles on this DVD.
There are 21 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
audio stream: 2 format: ac3 (5.1) language: es aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
number of subtitles on disk: 3
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
A:   0.3 V:   0.3 A-V:  0.073 ct:  0.009  10/  8 ??% ??% ??,?% 0 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.9% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.9% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.8% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
No bind found for key 'MOUSE_BTN0'.                         6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)1.6% 0 0 
GNOME screensaver enabled

Exiting... (Quit)
mom@mom-laptop:~$ 

this is what I got when I started the movie through the terminal.

---

### Post by peppino on 2009-03-17
What kind of dvd a copy or a real dvd

---

### Post by Nano_ext3 on 2009-03-17
Make life easy on you and get VLC , via Add/Remove or in terminal by doing "sudo apt-get install vlc"

Cheers


-Nano

---

### Post by dstanfel on 2009-03-17
I have tried several store bought dvd's with no luck. I have tried to install vlc and it will not work either. I have followed the steps in other forums for installing with no luck.

---

### Post by dstanfel on 2009-03-17
I have already tried installing vlc several times and i get the same results. I have yet to find out what it is I am doing wrong. I have tried following the steps in other forums for installing the different dvd players and i end up with the same results I have sound but no picture on smplayer and vlc and the others will not even open.

---

### Post by rvm4000 on 2009-03-17
For some reason xv is not working properly in your system. You need to configure the players to use a different one. In smplayer go to Preferences -> General -> Video and select x11 or gl as video driver instead of xv.

---

### Post by Ericyzfr1 on 2009-03-17
Have you checked the Ubuntu Community Documentation? It seems that you have something is missing.

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)   then search for playing DVD's

---

### Post by Ericyzfr1 on 2009-03-17
Something I went through before with another distro, do you have the right screen resolution?
I used Kaffeine with Mandriva/ KDE and my screen resolution was not set properly preventing me from playing DVD's.

---

### Post by dstanfel on 2009-03-17
tried altering the screen res on all the players when I first tried to get them to work and it did nothing. This is enough to drive a person crazy.

---

### Post by Ericyzfr1 on 2009-03-17
Since it seems the symptom is common to all players, I would refer you to the link on my previous post....It could be really worth it to have a look.

---

### Post by dstanfel on 2009-03-17
that worked I changed it from xv to xll and it worked I now have smplayer that actually plays the video along with the sound. Thank you so very much for your help.

---

