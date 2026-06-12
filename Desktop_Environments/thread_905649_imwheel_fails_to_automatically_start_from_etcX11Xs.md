---
title: "imwheel fails to automatically start from /etc/X11/Xsesssion.d"
date: 2008-08-30
forum: Desktop Environments
---

### Post by dragisak on 2008-08-30
I am trying to automatically start imwheel whenever I start my desktop.

I've changed /etc/X11/imwheel/startup.conf like this:

```
IMWHEEL_START=1
IMWHEEL_PARAMS='-k'
```

/etc/X11/Xsession.d/60imwheel_start-imwheel file is there and I can invoke it from command line.

But imwheel is not working when I log in. 

I haven't looked in ~/.xsession-errors before and it shows bunch of errors (I have no problems with my desktop environment). The second line shows that imwheel is started but ps -ef doesn't show that it's running. It works fine if I invoke it from command line.


```
/etc/gdm/Xsession: Beginning session setup...
INFO: imwheel started (pid=6248)
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/blastocyst:/tmp/.ICE-unix/6134

** (gnome-settings-daemon:6266): WARNING **: The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
expected keysym, got XF86KbdLightOnOff: line 70 of pc
last scanned symbol is: XF86KbdLightOnOff
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
last scanned symbol is: XF86KbdBrightnessDown
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
last scanned symbol is: XF86KbdBrightnessUp
Warning:          Type "PC_RALT_LEVEL2" has 2 levels, but <LALT> has 3 symbols
                  Ignoring extra symbols
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)
Warning:          No symbols defined for <FK16> (keycode 121)
Warning:          No symbols defined for <FK17> (keycode 122)
Warning:          No symbols defined for <KPDC> (keycode 123)
Warning:          No symbols defined for <XFER> (keycode 129)
Warning:          No symbols defined for <I02> (keycode 130)
Warning:          No symbols defined for <NFER> (keycode 131)
Warning:          No symbols defined for <I04> (keycode 132)
Warning:          No symbols defined for <AE13> (keycode 133)
Warning:          No symbols defined for <I06> (keycode 134)
Warning:          No symbols defined for <I07> (keycode 135)
Warning:          No symbols defined for <I08> (keycode 136)
Warning:          No symbols defined for <I09> (keycode 137)
Warning:          No symbols defined for <I0A> (keycode 138)
Warning:          No symbols defined for <I0B> (keycode 139)
Warning:          No symbols defined for <I0C> (keycode 140)
Warning:          No symbols defined for <I0D> (keycode 141)
Warning:          No symbols defined for <I0E> (keycode 142)
Warning:          No symbols defined for <I0F> (keycode 143)
Warning:          No symbols defined for <I10> (keycode 144)
Warning:          No symbols defined for <I11> (keycode 145)
Warning:          No symbols defined for <I12> (keycode 146)
Warning:          No symbols defined for <I13> (keycode 147)
Warning:          No symbols defined for <I14> (keycode 148)
Warning:          No symbols defined for <I15> (keycode 149)
Warning:          No symbols defined for <I16> (keycode 150)
Warning:          No symbols defined for <I17> (keycode 151)
Warning:          No symbols defined for <I18> (keycode 152)
Warning:          No symbols defined for <I19> (keycode 153)
Warning:          No symbols defined for <I1A> (keycode 154)
Warning:          No symbols defined for <I1B> (keycode 155)
Warning:          No symbols defined for <K59> (keycode 157)
Warning:          No symbols defined for <I1E> (keycode 158)
Warning:          No symbols defined for <I1F> (keycode 159)
Warning:          No symbols defined for <I20> (keycode 160)
Warning:          No symbols defined for <I21> (keycode 161)
Warning:          No symbols defined for <I22> (keycode 162)
Warning:          No symbols defined for <I23> (keycode 163)
Warning:          No symbols defined for <I24> (keycode 164)
Warning:          No symbols defined for <I25> (keycode 165)
Warning:          No symbols defined for <I26> (keycode 166)
Warning:          No symbols defined for <I27> (keycode 167)
Warning:          No symbols defined for <I28> (keycode 168)
Warning:          No symbols defined for <I29> (keycode 169)
Warning:          No symbols defined for <K5A> (keycode 170)
Warning:          No symbols defined for <I2B> (keycode 171)
Warning:          No symbols defined for <I2C> (keycode 172)
Warning:          No symbols defined for <I2D> (keycode 173)
Warning:          No symbols defined for <I2E> (keycode 174)
Warning:          No symbols defined for <I2F> (keycode 175)
Warning:          No symbols defined for <I30> (keycode 176)
Warning:          No symbols defined for <I31> (keycode 177)
Warning:          No symbols defined for <I32> (keycode 178)
Warning:          No symbols defined for <I33> (keycode 179)
Warning:          No symbols defined for <I34> (keycode 180)
Warning:          No symbols defined for <K5B> (keycode 181)
Warning:          No symbols defined for <K5D> (keycode 182)
Warning:          No symbols defined for <K5E> (keycode 183)
Warning:          No symbols defined for <K5F> (keycode 184)
Warning:          No symbols defined for <I39> (keycode 185)
Warning:          No symbols defined for <I3A> (keycode 186)
Warning:          No symbols defined for <I3B> (keycode 187)
Warning:          No symbols defined for <I3C> (keycode 188)
Warning:          No symbols defined for <K62> (keycode 189)
Warning:          No symbols defined for <K63> (keycode 190)
Warning:          No symbols defined for <K64> (keycode 191)
Warning:          No symbols defined for <K65> (keycode 192)
Warning:          No symbols defined for <K66> (keycode 193)
Warning:          No symbols defined for <I42> (keycode 194)
Warning:          No symbols defined for <I43> (keycode 195)
Warning:          No symbols defined for <I44> (keycode 196)
Warning:          No symbols defined for <I45> (keycode 197)
Warning:          No symbols defined for <K67> (keycode 198)
Warning:          No symbols defined for <K68> (keycode 199)
Warning:          No symbols defined for <K69> (keycode 200)
Warning:          No symbols defined for <K6A> (keycode 201)
Warning:          No symbols defined for <I4A> (keycode 202)
Warning:          No symbols defined for <K6B> (keycode 203)
Warning:          No symbols defined for <K6C> (keycode 204)
Warning:          No symbols defined for <K6D> (keycode 205)
Warning:          No symbols defined for <K6E> (keycode 206)
Warning:          No symbols defined for <K6F> (keycode 207)
Warning:          No symbols defined for <HKTG> (keycode 208)
Warning:          No symbols defined for <KANA> (keycode 209)
Warning:          No symbols defined for <EISU> (keycode 210)
Warning:          No symbols defined for <AB11> (keycode 211)
Warning:          No symbols defined for <I54> (keycode 212)
Warning:          No symbols defined for <I55> (keycode 213)
Warning:          No symbols defined for <I5A> (keycode 218)
Warning:          No symbols defined for <K74> (keycode 219)
Warning:          No symbols defined for <K75> (keycode 220)
Warning:          No symbols defined for <K76> (keycode 221)
Warning:          No symbols defined for <I5E> (keycode 222)
Warning:          No symbols defined for <I5F> (keycode 223)
Warning:          No symbols defined for <I60> (keycode 224)
Warning:          No symbols defined for <I61> (keycode 225)
Warning:          No symbols defined for <I62> (keycode 226)
Warning:          No symbols defined for <I63> (keycode 227)
Warning:          No symbols defined for <I64> (keycode 228)
Warning:          No symbols defined for <I65> (keycode 229)
Warning:          No symbols defined for <I66> (keycode 230)
Warning:          No symbols defined for <I67> (keycode 231)
Warning:          No symbols defined for <I68> (keycode 232)
Warning:          No symbols defined for <I69> (keycode 233)
Warning:          No symbols defined for <I6A> (keycode 234)
Warning:          No symbols defined for <I6B> (keycode 235)
Warning:          No symbols defined for <I6C> (keycode 236)
Warning:          No symbols defined for <I6D> (keycode 237)
Warning:          No symbols defined for <I6E> (keycode 238)
Warning:          No symbols defined for <I6F> (keycode 239)
Warning:          No symbols defined for <I70> (keycode 240)
Warning:          No symbols defined for <I71> (keycode 241)
Warning:          No symbols defined for <I72> (keycode 242)
Warning:          No symbols defined for <I73> (keycode 243)
Warning:          No symbols defined for <I74> (keycode 244)
Warning:          No symbols defined for <I75> (keycode 245)
Warning:          No symbols defined for <I76> (keycode 246)
Warning:          No symbols defined for <I77> (keycode 247)
Warning:          No symbols defined for <I78> (keycode 248)
Warning:          No symbols defined for <I79> (keycode 249)
Warning:          No symbols defined for <I7A> (keycode 250)
Warning:          No symbols defined for <I7B> (keycode 251)
Warning:          No symbols defined for <I7C> (keycode 252)
Warning:          No symbols defined for <I7D> (keycode 253)
Warning:          No symbols defined for <I7E> (keycode 254)
Warning:          No symbols defined for <I7F> (keycode 255)
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/dragisak/.metacity/sessions/default0.ms: Failed to open file '/home/dragisak/.metacity/sessions/default0.ms': No such file or directory


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD
11
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 17050 1220140800 1220123750
evolution-alarm-notify-Message:  Sat Aug 30 17:00:00 2008

evolution-alarm-notify-Message:  Sat Aug 30 12:15:50 2008

seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6299): WARNING **: Unable to add monitor: Not supported
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  PID TTY          TIME CMD
 6278 ?        00:00:00 pulseaudio
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Any ideas ?

---

