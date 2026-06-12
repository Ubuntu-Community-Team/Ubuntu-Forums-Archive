---
title: "xfce sound id for event?"
date: 2015-10-26
forum: Debian
---

### Post by virgosun on 2015-10-26
[COLOR=#333333][FONT=Verdana][SIZE=2][FONT=arial]Hi all,
I am installing canberra for event sound and input feed back sound
I installed freedesktop sound theme and moblin
All sound files are there
but only trash empty event trigger sound.
other events like: login, dialog error , etc etc no sound...
for login I created login.ogg link to destop-login.ogg but
canberra-gtk-play claim unknown event id?
pls help
I like to have startup sound at xfce login and other event[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by howefield on 2015-10-26
Thread moved to the "*Debian*" forum.

---

### Post by Toz on 2015-10-26
Lets first confirm a few settings:
```
xfconf-query -c xsettings -p /Net/SoundThemeName
env | grep GTK_MODULE
xfconf-query -c xsettings -p /Net/EnableEventSounds
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
```

Secondly, you need to be aware that the canberra implementation only supports a [few sound events]("http://git.0pointer.net/libcanberra.git/tree/src/canberra-gtk-module.c"):
> /*
We generate these sounds:

dialog-error
dialog-warning
dialog-information
dialog-question
window-new
window-close
window-minimized
window-unminimized
window-maximized
window-unmaximized
notebook-tab-changed
dialog-ok
dialog-cancel
item-selected
link-pressed
link-released
button-pressed
button-released
menu-click
button-toggle-on
button-toggle-off
menu-popup
menu-popdown
menu-replace
tooltip-popup
tooltip-popdown
drag-start
drag-accept
drag-fail
expander-toggle-on
expander-toggle-off

TODO:
scroll-xxx
window-switch
window-resize-xxx
window-move-xxx

*/ 

And finally, Xfce doesn't have a built-in mechanism for playing a login sound. You need to create an Application Autostart entry to play the login sound.

---

### Post by virgosun on 2015-10-26
Thanks Toz

You make it clear that no built-in login sound event on xfce
My canberra sound works
Apparently I have only a few sound file correspond to which supported by canberra 
Besides emptying trash, adjusting volume in pavucontrol also trigger event sound
I haven't discovered more..
I think the default theme name is just a priority in case there are multiple sound files with the same name
To enable sound event I can also set in GUI  App Menu-> Setting-> Appearance->Setting->Event Sound
However to make sure...

```

virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/SoundThemeName
moblin

virgosun@GlobeTravelers:~$ env | grep GTK_MODULE
GTK_MODULES=canberra-gtk-module:gail:atk-bridge

virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/EnableEventSounds
true
virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
true

```



```

virgosun@GlobeTravelers:~$ find /usr/share/sounds/ -type l -o -type f

```
[file]
/usr/share/sounds/alsa/Front_Right.wav
/usr/share/sounds/alsa/Front_Left.wav
/usr/share/sounds/alsa/Side_Left.wav
/usr/share/sounds/alsa/Side_Right.wav
/usr/share/sounds/alsa/Front_Center.wav
/usr/share/sounds/alsa/Noise.wav
/usr/share/sounds/alsa/Rear_Center.wav
/usr/share/sounds/alsa/Rear_Right.wav
/usr/share/sounds/alsa/Rear_Left.wav
/usr/share/sounds/freedesktop/stereo/alarm-clock-elapsed.oga
/usr/share/sounds/freedesktop/stereo/phone-outgoing-calling.oga
/usr/share/sounds/freedesktop/stereo/dialog-error.oga
/usr/share/sounds/freedesktop/stereo/window-attention.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-side-left.oga
/usr/share/sounds/freedesktop/stereo/device-added.oga
/usr/share/sounds/freedesktop/stereo/dialog-information.oga
/usr/share/sounds/freedesktop/stereo/message-new-instant.oga
/usr/share/sounds/freedesktop/stereo/audio-volume-change.oga
/usr/share/sounds/freedesktop/stereo/screen-capture.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-front-right.oga
/usr/share/sounds/freedesktop/stereo/audio-test-signal.oga
/usr/share/sounds/freedesktop/stereo/device-removed.oga
/usr/share/sounds/freedesktop/stereo/bell.oga
/usr/share/sounds/freedesktop/stereo/suspend-error.oga
/usr/share/sounds/freedesktop/stereo/power-plug.oga
/usr/share/sounds/freedesktop/stereo/window-question.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-side-right.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-rear-right.oga
/usr/share/sounds/freedesktop/stereo/power-unplug.oga
/usr/share/sounds/freedesktop/stereo/dialog-warning.oga
/usr/share/sounds/freedesktop/stereo/phone-outgoing-busy.oga
/usr/share/sounds/freedesktop/stereo/camera-shutter.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-front-left.oga
/usr/share/sounds/freedesktop/stereo/network-connectivity-lost.oga
/usr/share/sounds/freedesktop/stereo/trash-empty.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-front-center.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-rear-left.oga
/usr/share/sounds/freedesktop/stereo/complete.oga
/usr/share/sounds/freedesktop/stereo/network-connectivity-established.oga
/usr/share/sounds/freedesktop/stereo/audio-channel-rear-center.oga
/usr/share/sounds/freedesktop/stereo/message.oga
/usr/share/sounds/freedesktop/stereo/service-login.oga
/usr/share/sounds/freedesktop/stereo/service-logout.oga
/usr/share/sounds/freedesktop/stereo/phone-incoming-call.oga
/usr/share/sounds/freedesktop/index.theme
/usr/share/sounds/moblin/stereo/phone-hangup.wav
/usr/share/sounds/moblin/stereo/battery-low.wav
/usr/share/sounds/moblin/stereo/suspend-start.wav
/usr/share/sounds/moblin/stereo/power-unplug-battery-low.wav
/usr/share/sounds/moblin/stereo/dialog-error.wav
/usr/share/sounds/moblin/stereo/phone-incoming-call.wav
/usr/share/sounds/moblin/stereo/window-attention-inactive.wav
/usr/share/sounds/moblin/stereo/bell-window-system.wav
/usr/share/sounds/moblin/stereo/battery-caution.wav
/usr/share/sounds/moblin/stereo/audio-test-signal.ogg
/usr/share/sounds/moblin/stereo/phone-failure.wav
/usr/share/sounds/moblin/stereo/trash-empty.wav
/usr/share/sounds/moblin/stereo/suspend-resume.wav
/usr/share/sounds/moblin/stereo/message-new-email.wav
/usr/share/sounds/moblin/stereo/drag-fail.wav
/usr/share/sounds/moblin/stereo/phone-outgoing-busy.wav
/usr/share/sounds/moblin/stereo/bell-terminal.wav
/usr/share/sounds/moblin/stereo/device-removed.wav
/usr/share/sounds/moblin/stereo/dialog-question.wav
/usr/share/sounds/moblin/stereo/alarm-clock-elapsed.wav
/usr/share/sounds/moblin/stereo/power-unplug.wav
/usr/share/sounds/moblin/stereo/device-added.wav
/usr/share/sounds/moblin/stereo/dialog-warning.wav
/usr/share/sounds/moblin/stereo/double-very-low.wav
/usr/share/sounds/moblin/stereo/audio-volume-change.wav
/usr/share/sounds/moblin/stereo/camera-shutter.wav
/usr/share/sounds/moblin/stereo/suspend-error.wav
/usr/share/sounds/moblin/stereo/screen-capture.wav
/usr/share/sounds/moblin/stereo/count-down.wav
/usr/share/sounds/moblin/stereo/desktop-login.ogg
/usr/share/sounds/moblin/stereo/single-very-low.wav
/usr/share/sounds/moblin/stereo/message-new-instant.wav
/usr/share/sounds/moblin/stereo/item-deleted.wav
/usr/share/sounds/moblin/index.theme


[/file]

Can you suggest some theme with more sound event

By the way, I have tried to enable tone beep in grub boot but it seem as-thought my system don't load pcspeaker module 
Which steps should I follow
Thanks

---

### Post by Toz on 2015-10-26
> **virgosun said:**
> However to make sure...

```

virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/SoundThemeName
moblin

virgosun@GlobeTravelers:~$ env | grep GTK_MODULE
GTK_MODULES=canberra-gtk-module:gail:atk-bridge

virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/EnableEventSounds
true
virgosun@GlobeTravelers:~$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
true

```
Settings look good.

> Can you suggest some theme with more sound event
I'm not aware of one. I've created my own in the past when I've used sound events and you can as well. Here is what you can do:
1. Create a local sounds directory:
```
mkdir -p ~/.local/share/sounds
```
2. Copy over the moblin theme to your local sounds directory:
```
cp -rv /usr/share/sounds/moblin ~/.local/share/sounds
```
3. Rename the sound files in ~/.local/share/sounds/moblin/stereo to match the canberra-support sound events

Note: I have found that in some cases, even if the canberra implementation says it supports a sound event, that the sound does not occur. Trial and error should help you to get the most of the events to generate sounds.

> By the way, I have tried to enable tone beep in grub boot but it seem as-thought my system don't load pcspeaker module 
Which steps should I follow
To be honest, I do not know. Perhaps you can create another thread for this question.

---

### Post by virgosun on 2015-10-26
> **Toz said:**
> Settings look good.


I'm not aware of one. I've created my own in the past when I've used sound events and you can as well. Here is what you can do:
1. Create a local sounds directory:
```
mkdir -p ~/.local/share/sounds
```
2. Copy over the moblin theme to your local sounds directory:
```
cp -rv /usr/share/sounds/moblin ~/.local/share/sounds
```
3. Rename the sound files in ~/.local/share/sounds/moblin/stereo to match the canberra-support sound events

Note: I have found that in some cases, even if the canberra implementation says it supports a sound event, that the sound does not occur. Trial and error should help you to get the most of the events to generate sounds.


To be honest, I do not know. Perhaps you can create another thread for this question.

Thank Toz

make ~/.local/share/sounds dir works.
Now I can hear many more event sound.
But events sound only with built-in apps, ie thunar file manager , terminal window-maximized work whistle uxterm or chromium... not work

Sun

---

### Post by Toz on 2015-10-26
> **virgosun said:**
> whistle uxterm or chromium... not work
The applications themselves need to support the libcanberra gtk implementation to work. I'm guessing that these two don't.

---

