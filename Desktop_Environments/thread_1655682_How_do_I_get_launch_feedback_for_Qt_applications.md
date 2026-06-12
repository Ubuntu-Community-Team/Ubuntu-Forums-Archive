---
title: "How do I get launch feedback for Qt applications?"
date: 2010-12-30
forum: Desktop Environments
---

### Post by Dobro_player on 2010-12-30
How do I get launch feedback for Qt applications such as VLC? For example, if I open a file with a gtk application the mouse turns into a spinning thing to show the application is loading, but this does not happen with Qt applications.

---

### Post by Dobro_player on 2010-12-30
No one knows? Should I file a bug report?

---

### Post by kellemes on 2011-01-01
Don't know this one.. so just a little guessing here..
You can configure launch-feedback from the KDE-settings-screen so you can install KDE's controlcenter (don't know what packages you need for this, probably a lot) to configure it..

But maybe there is a much easier way I don't know about..

---

### Post by Zorael on 2011-01-01
I don't think VLC would take cues from KDE settings when running under GNOME, seeing as it's just a Qt program and not a KDE one. I looked through **qtconfig** and there doesn't seem to be any setting there.

If you want to set the KDE setting nonetheless (and hope it does anything at all), just save the following file as **~/.kde/share/config/klaunchrc**;
```
[BusyCursorSettings]
Blinking=false
Bouncing=true

[FeedbackStyle]
BusyCursor=true
TaskbarButton=true

[TaskbarButtonSettings]
Timeout=20
```

Qt&#12399;KDE&#12398;&#12415;&#12354;&#12425;&#12378;

---

### Post by Dobro_player on 2011-01-12
I have noticed that launch feedback for VLC works under KDE, would it be possible to run whatever is responsible for launch feedback in KDE under gnome?

---

### Post by foxmulder881 on 2011-01-12
Just launch the application from a terminal and then post the output. This may help determine anything strange that's going on behind the scenes.

---

### Post by Dobro_player on 2011-01-13
This is the output from launching VLC in the terminal:
```
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb747e0d4, 0xb747e048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1294597107)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4536): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
```

---

### Post by foxmulder881 on 2011-01-13
> **Dobro_player said:**
> This is the output from launching VLC in the terminal:

<snip>

There doesn't appear to actually be anything 'wrong' as such. And your terminal launch output looks much the same as mine does. Although I have one more interesting line of output which I'm a little curious about. I have bolded in my output.

```
foxbox% vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
**[0xa55120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.**
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f8d27ef3b20, 0x7f8d27ef3a80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1294198189)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:12187): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
```

---

