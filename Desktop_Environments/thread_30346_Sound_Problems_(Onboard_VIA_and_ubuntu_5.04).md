---
title: "Sound Problems (Onboard VIA and ubuntu 5.04)"
date: 2005-04-28
forum: Desktop Environments
---

### Post by fidel castro on 2005-04-28
Hi,

im relativly new to the linux/OS and installed ubuntu (Kubuntu) 5.04.

Got some heavy problems with my onboard sound.


Some infos:
//////////////////////////////////////////
1. Discover Sound Output:

VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller


///////////////////////////////////////////////////////////
2.  Output from amarok as test player:

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QObject::connect: Cannot connect Engine::Base::statusText( const QString& ) to (null)::shortMessage( const QString& )
QObject::connect: Cannot connect Engine::Base::infoMessage( const QString& ) to (null)::longMessage( const QString& )
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
fidel@irak:~$ QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )


///////////////////////////////////////////////////
3. Output from: cat /proc/asound/cards; amixer

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650E at 0xe000, irq 6
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 24 [77%] [on]
  Front Right: Playback 22 [71%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on]
  Front Right: Playback 22 [71%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [off]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line-In As Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on] Capture [off]
  Front Right: Playback 22 [71%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic As Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Input Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities:
  Mono:
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Input Source Select',0
  Capabilities:
  Mono:
Simple mixer control 'Input Source Select',1
  Capabilities:
  Mono:
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'VIA DXS',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]
Simple mixer control 'VIA DXS',1
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]
Simple mixer control 'VIA DXS',2
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]
Simple mixer control 'VIA DXS',3
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]



atm i dont know how to handle this problem.
The only sound i can produce is with:

- aplay and WAV files
or
- changing sound in Controllcenter  to OSS, 
  but the mp3 output using OSS stutters


any ideas ?


greetings 
fidel

---

### Post by NaplesBill on 2005-04-28
[http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211) 

Look for my post regarding alsamixergui!  Worked for me and I also have a VIA sound chipset.

---

### Post by fidel castro on 2005-04-28
hi and thanks,

going to test it, when im back on my pc/ubuntu.
would be great if this is the solution.

looking forward

fidel

---

