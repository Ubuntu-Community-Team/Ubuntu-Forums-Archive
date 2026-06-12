---
title: "Change system volume from terminal"
date: 2017-11-24
forum: Desktop Environments
---

### Post by shag00 on 2017-11-24
Does anybody know if there is a terminal command to control/alter the volume in ubuntu 17.10?

---

### Post by again? on 2017-11-24
See if you can set a volume percentage with this command.
```
pactl -- set-sink-volume $(pacmd dump | awk '/set-sink-volume/{print $2}') **50%**
```

---

### Post by shag00 on 2017-11-24
comes back with message: "Invalid volume specification"

---

### Post by again? on 2017-11-24
What does this output?
```
pacmd dump | grep set-sink-volume
```

Also try to set volume with...
```
pactl -- set-sink-volume [COLOR="#FF0000"]0[/COLOR] 50%
```
or
```
pactl -- set-sink-volume [COLOR="#FF0000"]1[/COLOR] 50%
```

---

### Post by shag00 on 2017-11-24
```
pacmd dump | grep set-sink-volume
```

set-sink-volume alsa_output.pci-0000_00_03.0.hdmi-stereo 0x10000
set-sink-volume alsa_output.pci-0000_00_1b.0.iec958-stereo 0x10000

```
pactl -- set-sink-volume [COLOR=#FF0000]0[/COLOR] 50%
```

No output.

```
pactl -- set-sink-volume [COLOR=#FF0000]1[/COLOR] 50%
```

No output but DID change the volume.

---

### Post by again? on 2017-11-24
Ok, so you can probably use...
```
pactl -- set-sink-volume alsa_output.pci-0000_00_1b.0.iec958-stereo 50%
```
or a percentage to your liking.
See "man pactl".

What are you trying to do?
I have an old script here that still seems to work.
Allows you to increase/decrease volume in increments or toggle mute.

---

### Post by shag00 on 2017-11-24
guber2, thanks very much for your assistance, I note this is not the first time you have helped me.

I want to use this command with (invoked by) kshutdown, the reason being that I need the TV on to get to sleep (to many years spent flying internationally). So my nightly routine is to fall asleep to Al Jazeera but being a streamed service it needs a lot of volume to be audible. The problem is the next morning when powering on the PC, the startup sounds are way to loud and wakes up the wife. So I thought if I could get kshutdown to turn the volume to a low level while it is shutting down I could use the PC while my wife is still sleeping. So basically set sound (volume) to around 10-20%.

 If you have a prepaid script that would be wonderful.

Thanks.

---

### Post by ajgreeny on 2017-11-24
> Pulseaudio Volume commands for keyboard shortcuts.

pactl set-sink-volume @DEFAULT_SINK@ -5%		Lower volume by 5%

pactl set-sink-volume @DEFAULT_SINK@ +5%		Raise volume by 5%

pactl set-sink-mute @DEFAULT_SINK@ toggle		Toggle mute volume
The above is a note I have kept of my system's keyboard shortcuts to raise/lower/mute the volume of my system; it does, of course, work only if you are using pulseaudio, but I find those keyboard commands incredibly useful, rather than go to the volume settings GUI.

I have no idea what the default command is in kshutdown but I presume you are able to change it or if not create another custom shortcut to shutdown the system with command ```
pactl -- set-sink-volume 1 50% && shutdown -h now
```
I have setup a shutdown keyboard shortcut, though without that volume setting, which uses the Pause/Break+Winkey which is another one that I use a lot.

---

### Post by vasa1 on 2017-11-24
> **ajgreeny said:**
> ...
I have no idea what the default command is in kshutdown ...
There's a man page for it here: [http://manpages.ubuntu.com/manpages/artful/en/man1/kshutdown.1.html](http://manpages.ubuntu.com/manpages/artful/en/man1/kshutdown.1.html)

and *apt show kshutdown* has:```
Description: advanced shut down utility for KDE
 It has 4 main commands:
 .
  - Shut Down (logout and halt the system),
  - Reboot (logout and reboot the system),
  - Lock Screen (lock the screen using a screen saver),
  - Logout (end the session and logout the user).
 .
 It features time and delay options, command line support, wizard,
 and sounds.
```So I'm guessing OP can chain a suitable command ahead of kshutdown and ensure domestic peace!

---

### Post by shag00 on 2017-11-25
Thank you gentlemen for your input. I never realised that kshutdown only gives you the option to run an 'extra' (script) or shutdown not do both at the same time which is a bit sad. Anyway, I settled on the following command inside a script:
```
gnome-terminal -x sh -c 'killall firefox; echo TO CANCEL SHUTDOWN USE   shutdown -c; shutdown; pactl -- set-sink-volume 1 20%; exec bash'
```
This does, in order: opens a terminal, stop Firefox, prints shutdown cancel instructions in the terminal, initiates shutdown in 1 minute and lastly sets the volume to 20%.

---

### Post by again? on 2017-11-25
I wanted a simple timed shutdown for myself so
created a launcher for your script if you want to use.

```
gedit ~/.local/share/applications/shutdown-delay.desktop
```
Copy and paste in the following.
```
[Desktop Entry]
Name=Shutdown-Delay
Exec=[COLOR="#FF0000"]/home/glen/scripts/aatest.sh[/COLOR]
Icon=[COLOR="#FF8C00"]/home/glen/Documents/icons/shutdown-delay.png[/COLOR]
Type=Application
Categories=Utility;
StartupNotify=false
Keywords=shutdown;timer;sleep;

Actions=cancel;

[Desktop Action cancel]
Name=Cancel Shutdown
Exec=shutdown -c
```
Edit for [COLOR="#FF0000"]your script path[/COLOR] and [COLOR="#FF8C00"]icon path[/COLOR](see attached icon).

Make the .desktop file executable.
```
chmod +x ~/.local/share/applications/shutdown-delay.desktop
```

Search the applications overlay for "shutdown" and Add to Favourites.

Right clicking the launcher icon will show a cancel item.

---

### Post by shag00 on 2017-11-25
guber2, thanks for that. Your icon is a dam sight better than kshutdown's.

---

