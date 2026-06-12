---
title: "No sound in KDE Plasma"
date: 2017-08-01
forum: Desktop Environments
---

### Post by dmitriano on 2017-08-01
I have no sound in KDE Plama, and playback devices are grey:

[IMG]https://developernote.com/wp-content/uploads/2017/08/kde-no-sound.png[/IMG]

what can be wrong? Any ideas?

---

### Post by #&amp;thj^% on 2017-08-01
What is the return of this from the terminal:
```
pactl info
```

---

### Post by vasa1 on 2017-08-01
> **dmitriano said:**
> I have no sound in KDE Plama, and playback devices are grey:

[IMG]https://developernote.com/wp-content/uploads/2017/08/kde-no-sound.png[/IMG]

what can be wrong? Any ideas?
Are you using a pure KDE system such as Kubuntu or KDE Neon or is your system a mish-mash of desktop environments?

What do you have in */usr/share/xsessions*?

---

### Post by dmitriano on 2017-08-01
The output of
```

pactl info

```

is:

Server String: unix:/run/user/1002/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 40
Tile Size: 65472
User Name: dmitry
Host Name: Asus
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: auto_null
Default Source: auto_null.monitor
Cookie: f35c:6d81

---

### Post by dmitriano on 2017-08-01
I have multiple desktops:

nome-classic.desktop  gnome.desktop  kde-plasma.desktop  ubuntu.desktop

---

### Post by #&amp;thj^% on 2017-08-01
> **dmitriano said:**
> The output of
```

pactl info

```

is:

Server String: unix:/run/user/1002/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 40
Tile Size: 65472
User Name: dmitry
Host Name: Asus
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: auto_null
Default Source: auto_null.monitor
Cookie: f35c:6d81
I keep forgetting you have multiple DE's and they can/will cause conflicts with underlying utilities.
But your problem is:
```
Default Sink: auto_null
Default Source: auto_null.monitor
```
Do you have pusleaudio volume control (pavucontrol) installed?

---

### Post by dmitriano on 2017-08-01
Yes, I have multiple DE, and now I start them manually from the terminal using startx:

```

startx $(which startkde)
startx $(which gnome-sesstion)

```

because finally I [returned Nvidia driver]("https://developernote.com/2017/07/using-qapitrace/"), but if I log in with graphical screen, the other 3rd party driver is used for some reason.

I have no sound on all DEs, and GNOME also shows this:

Server String: /run/user/1002/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 50
Tile Size: 65472
User Name: dmitry
Host Name: Asus
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: auto_null
Default Source: auto_null.monitor
Cookie: f35c:6d81

FIGURED THIS OUT! The sound is initialized ONLY when I log in with graphical screen!

And your command shows the following:

Server String: unix:/run/user/1002/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 28
Tile Size: 65472
User Name: dmitry
Host Name: Asus
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: ba00:d059

The only question is what prevent sound from being initialized if I start DE manually?

I intalled pavucontrol.

---

