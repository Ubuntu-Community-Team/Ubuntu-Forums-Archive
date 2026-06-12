---
title: "many notifications"
date: 2011-06-09
forum: Desktop Environments
---

### Post by go8765 on 2011-06-09
hello. help me please with notifications. when i chaged my volume with hotkeys i need only one notification that changed, but not many notifications. can i do it with xface4-notifyd ? (i need volume notifications such as in notification-daemoon or notify-osd. but notification-daemoon didnt suport thems and looklike not very good. and notify-osd is wery slow for me...)

---

### Post by hhh on 2011-06-09
Not sure what you mean by many notifications, but xfce4-notifyd...
[http://packages.ubuntu.com/natty/xfce4-notifyd](http://packages.ubuntu.com/natty/xfce4-notifyd)

For enabling keyboard controls you need xfce4-volumed...
[http://packages.ubuntu.com/natty/xfce4-volumed](http://packages.ubuntu.com/natty/xfce4-volumed)

For setting up keyboard shortcuts (I don't know if this works with pulseaudio though, I know it works with alsa)...
[https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons](https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons)

---

### Post by go8765 on 2011-06-10
> **hhh said:**
> Not sure what you mean by many notifications, but xfce4-notifyd...
[http://packages.ubuntu.com/natty/xfce4-notifyd](http://packages.ubuntu.com/natty/xfce4-notifyd)

For enabling keyboard controls you need xfce4-volumed...
[http://packages.ubuntu.com/natty/xfce4-volumed](http://packages.ubuntu.com/natty/xfce4-volumed)

For setting up keyboard shortcuts (I don't know if this works with pulseaudio though, I know it works with alsa)...
[https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons](https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons)
i mean this

---

### Post by hhh on 2011-06-10
Wow, that is one annoying looking bug!! Does that happen after every reboot? Something is really wrong there, that's not how notify-osd is supposed to behave.

---

### Post by go8765 on 2011-06-10
> **hhh said:**
> Wow, that is one annoying looking bug!! Does that happen after every reboot? Something is really wrong there, that's not how notify-osd is supposed to behave.

sory... but english is not my native language and i know it bed.can you simply write your answer? do you know how to fit this "many" notifications?
i see it everytyme, when i change volyme with hotkey.
this is part of my rc.html (i use openbox session):
<keybind key="C-Up">
      <action name="Execute">
        <execute>amixer -q set PCM 10+</execute>
      </action>
      <action name="Execute">
        <execute>~/bin/volume-notify</execute>
      </action>
    </keybind>
    <keybind key="C-Down">
      <action name="Execute">
        <execute>amixer -q set PCM 10-</execute>
      </action>
      <action name="Execute">
        <execute>~/bin/volume-notify</execute>
      </action>
    </keybind>
p.s. whet i use notification-daemoon or notify-osd i see only one notification that changed, but not many notifications such i see it in xface4-notifyd...

---

### Post by hhh on 2011-06-10
> **go8765 said:**
> p.s. whet i use notification-daemoon or notify-osd i see only one notification that changed, but not many notifications such i see it in xface4-notifyd...
I'm sorry, I thought the problem was with notify-osd, so my answer was to use xfce4-notifyd. Since notify-osd works, I'd say use it, but you say it's slow.

Have you tried completely removing xfce4-notifyd and reinstalling, then rebooting?

---

### Post by go8765 on 2011-06-11
> **hhh said:**
> I'm sorry, I thought the problem was with notify-osd, so my answer was to use xfce4-notifyd. Since notify-osd works, I'd say use it, but you say it's slow.

Have you tried completely removing xfce4-notifyd and reinstalling, then rebooting?

yes. i do  it now but it didnt help...:(

---

### Post by Toz on 2011-06-11
> **go8765 said:**
> sory... but english is not my native language and i know it bed.can you simply write your answer? do you know how to fit this "many" notifications?
i see it everytyme, when i change volyme with hotkey.
this is part of my rc.html (i use openbox session):
<keybind key="C-Up">
      <action name="Execute">
        <execute>amixer -q set PCM 10+</execute>
      </action>
      <action name="Execute">
        <execute>~/bin/volume-notify</execute>
      </action>
    </keybind>
    <keybind key="C-Down">
      <action name="Execute">
        <execute>amixer -q set PCM 10-</execute>
      </action>
      <action name="Execute">
        <execute>~/bin/volume-notify</execute>
      </action>
    </keybind>
p.s. whet i use notification-daemoon or notify-osd i see only one notification that changed, but not many notifications such i see it in xface4-notifyd...

xfce4-notify will automatically display volume notification changes if you use the Master channel (you are using PCM). Open a terminal window, and type in: ```
amixer -q set Master 10+
```Did the volume change? Do you get a notification?

I believe that if you changed your commands to control the Master channel and removed your custom notify scripts, you would get proper notifications. If this doesn't work and you _must_ manage the PCM channel to get volume changes, you'll need to setup pulseaudio so that PCM is your default channel.

---

### Post by neu5eeCh on 2011-06-11
Have you tried running "mixer"? ALT-F2 "Mixer". Take a look at what controls are activated there. It's possible that XFCE thinks you're adjusting the volume for a variety of audio output devices. Also, if you're not an OS purist, try installing the following:

[http://www.omgubuntu.co.uk/2011/05/recieve-ubuntu-notifications-when-connecting-usb-peripherals-with-udev-notify/](http://www.omgubuntu.co.uk/2011/05/recieve-ubuntu-notifications-when-connecting-usb-peripherals-with-udev-notify/)

I noticed that the notifier **also** replaced XFCE's other notifiers - which I didn't mind at all.

---

### Post by go8765 on 2011-06-11
> **Toz said:**
> xfce4-notify will automatically display volume notification changes if you use the Master channel (you are using PCM). Open a terminal window, and type in: ```
amixer -q set Master 10+
```Did the volume change? Do you get a notification?

I believe that if you changed your commands to control the Master channel and removed your custom notify scripts, you would get proper notifications. If this doesn't work and you _must_ manage the PCM channel to get volume changes, you'll need to setup pulseaudio so that PCM is your default channel.

thank you) its really help me) i change PCM to Master in my rc.html and now i see good xfce notify) the problem is solved) [[IMG]http://img221.imageshack.us/img221/9731/3035xg.th.png[/IMG]](http://img221.imageshack.us/i/3035xg.png/)

---

