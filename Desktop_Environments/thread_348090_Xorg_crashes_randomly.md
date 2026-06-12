---
title: "Xorg crashes randomly"
date: 2007-01-28
forum: Desktop Environments
---

### Post by supermihi on 2007-01-28
Hi,
on one of the (k)ubuntu boxes I administer (it's x86 edgy, up-to-date) since a few weeks the X-Server crashes every few days, without any apparent cause.

Here is the end of Xorg.0.log.old:

```
II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(ProcFreePixmap+0x79) [0x8080a62]
3: /usr/bin/X(Dispatch+0x19e) [0x8085d56]
4: /usr/bin/X(main+0x47c) [0x806e0d8]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d80ea2]
6: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

```

Any ideas what this could be? There are no (EE) lines in Xorg.log, only the error about not existent SecurityPolicy-file, but that should be uncritical?

---

