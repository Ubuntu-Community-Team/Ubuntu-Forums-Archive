---
title: "Keybindings for Fn-F1"
date: 2010-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pswoo on 2010-08-04
I've got another notebook which requires the function key (Fn) to be pressed in concert for any of the F(1-12) keys to work. Thus, on that notebook if I want to press F1 I actually press Fn-F1.

On my XPS (Ubuntu 9.10), however, use of the Fn key is not required - and pressing Fn-F1 will actually hibernate my computer immediately. I make this mistake fairly often, as I'm used to the motion from using my other notebook.

I've tried fooling around in 'System > Preferences > Keyboard shortcuts', to prevent Fn-F1 from causing a hibernate, but the keybinding doesn't seem to be there.

Know where I can find it?

---

### Post by simosx on 2010-08-04
Those keybindings (like Hibernate) should be specified in /lib/udev/keymaps/
You need to find the relevant model for your laptop for this. If you remove the lines, you can disable 'Hibernate', etc. Good luck and report back.

---

### Post by pswoo on 2010-08-04
Found it in /lib/udev/keymaps/dell.

```
$ cat /lib/udev/keymaps/dell
0x81 playpause # Play/Pause
0x82 stopcd # Stop
0x83 previoussong # Previous song
0x84 nextsong # Next song
0x85 brightnessdown # Fn+Down arrow Brightness Down
0x86 brightnessup # Fn+Up arrow Brightness Up
0x87 battery # Fn+F3 battery icon
0x88 wlan # Fn+F2 Turn On/Off Wireless
0x89 ejectclosecd # Fn+F10 Eject CD
0x8A suspend # Fn+F1 hibernate
0x8B switchvideomode # Fn+F8 CRT/LCD (high keycode: "displaytoggle")
0x8C f23 # Fn+Right arrow Auto Brightness
0x8F switchvideomode # Fn+F7 aspect ratio
0x90 previoussong # Front panel previous song
0x91 prog1 # Wifi Catcher (DELL Specific)
0x92 media # MediaDirect button (house icon)
0x93 f23 # FIXME Fn+Left arrow Auto Brightness
0x95 camera # Shutter button Takes a picture if optional camera available
0x97 email # Tablet email button
0x98 f21 # FIXME: Tablet screen rotatation
0x99 nextsong # Front panel next song
0x9A setup # Tablet tools button
0x9B switchvideomode # Display Toggle button
0xA2 playpause # Front panel play/pause
0xA4 stopcd # Front panel stop
0xD8 screenlock # FIXME: Tablet lock button
0xED media # MediaDirect button
```

After changing to

```

...
0x8A battery # Fn+F1 hibernate
...

```

hitting Fn-F1 now harmlessly shows me my battery status. Thanks!
(I wasn't sure what I could write in to result in no-op, so I chose battery).

---

### Post by simosx on 2010-08-04
Nice. Now add [SOLVED] in the topic title so that other members will benefit from this question.

In general, if someone wants to make additions to udev (that is, personal changes), the place to do them is '/etc/udev'. However, I believe for your special case it's OK to make the changes in the system file. If there is a system update for the udev package in the future, you should remember to locate this 'dell' file again and redo the change.

---

