---
title: "upgraded from ubuntu11.04 to 11.10+XFCE, now dell volume buttons only partially work"
date: 2011-10-28
forum: Desktop Environments
---

### Post by FabianN on 2011-10-28
I was running Ubuntu 11.04 and upgraded to 11.10 and installed the 'xubuntu' package for XFCE and  been logging into the Xubuntu shell. This is on a Dell Inspiron 6000 laptop, and the volume control buttons don't fully work.

I can use the mute button to mute the sound, but I can not unmute the sound using the buttons. When I press the mute button to unmute the Indicator plugin will change as if it's no longer muted, but up in the notification area the volume control still indicates that the sound is muted (which it is) and I can only unmute the sound through the notification area's volume control.

Like so:
[IMG]http://i.imgur.com/ka8il.png[/IMG] b

And, while the up/down volume controls work, the two volumes applets from the notification area and indicator plugin are out-of-sync. The volume bar in the indicator plugin will be all the way down but the volume in the notification area will not be all the way down. Minor, but I think it may be part of the same issue.

---

### Post by Xo-Mige on 2011-11-05
I had the same problem but if you use the   gnome-settings-deamon  the volume keys should work  first you should ether remove xfce4-volumed or stop it from launching  so it does not interfere  and see about a bug report I hope I helped

---

### Post by vangop on 2011-11-05
how do you switch between gnome-settings-daemon and xfce4-volumed?
I have the latter running, and need the fix for this mute bug.
I've filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-volumed/+bug/886447").

---

### Post by Xo-Mige on 2011-11-05
OK I disabled the xfce4-volumed from starting at login and the xfce4-settings-helper, I don't know if that last part is necessary or not. I then have gnome-settings-daemon start at login.  this would disable the xfce4-keyboard shortcuts but as the gnome settings daemon provides shortcut handling this probably is not that big of a deal

---

### Post by vangop on 2011-11-09
I actually removed pulseaudio and have no problem with sound AT ALL.
I had much more serious sound issues, pulseaudio kept dying, usually during a skype call. No problem now!
Recommend you guys do the same, just use alsa.

---

### Post by Steve DL on 2011-11-13
Hi. I'm the xfce4-volumed developer.

xfce4-volumed is NOT compatible with Pulseaudio. Xubuntu 11.10 uses Pulseaudio by default, hence problems. If you want me to work on a Pulseaudio back-end for xfce4-volumed, please send an email to the xfce4 development mailing list and ask for Pulseaudio support in the back-end of xfce4-volumed AND xfce4-mixer, and I'll see with the other developers if we want to work on this or not (this will also depend on my workload, which is extremely high at the moment).

Besides, gnome-settings-daemon has NOTHING to do on a Xfce-based distribution. Sorry guys but I strongly disagree to this. Xfce provides several independent daemons that do the same job (among which xfce4-settings-helper and xfce4-volumed), these are integrated (at least partially or in future plans) with Xfce applications, these are designed around the philosophy of Xfce, the desktop environment that you are using. Thus, they are more likely to be now, and to stay in the future, more suitable to your needs.

---

### Post by Xo-Mige on 2011-11-15
After further research I found out that xfce4-volumed mutes alsa and pulseaudio but does not unmute pulse just alsa and hence the problem so after some google seaches I found a script on the crunchbang form that can toggle pulseaudio the original is [here]("http://crunchbanglinux.org/forums/topic/11392/pulseaudio-volume-control-with-media-keys/").

this is my modified script:

```
#!/bin/bash
#### Create ~/.pulse/mute if not exists
ls ~/.pulse/mute &> /dev/null
if [[ $? != 0 ]]
then
    echo "false" > ~/.pulse/mute
fi


MUTE=`cat ~/.pulse/mute`          #Reads mute state
        
    
if [[ $1 == "mute" ]]
then
    if [[ $MUTE == "false" ]]
    then
        pactl set-sink-mute 0 1
        echo "true" > ~/.pulse/mute
    exit    
    else
        pactl set-sink-mute 0 0
        echo "false" > ~/.pulse/mute    
    exit
    fi
fi

pactl set-sink-volume 0 $CURVOL
echo $CURVOL > ~/.pulse/volume # Write the new volume to disk to be read the next time the script is run.
```it can be run with: 'name-or-script' mute

I also launch xfce4-volumed: with this script

```
#! /bin/bash


sleep 1
xfce4-volumed
```


I have this run when I press my mute key. as to why I don't just remove pulse, the reason for that is that some games such as: **neverwinter nights**, and **quake 4** and **quake 2** work with pulse and not with alsa. Its also easier to mute individual programs with pulse.

---

### Post by LewisTM on 2011-11-15
Steve, I admire your integrity.
I would still have been nice to tell the Xubuntu people not to include Pulseaudio and avoid all those conflicts.
I can confirm that removing Pulse works quite well.
Which brings the question: Who needs Pulseaudio? And does it deserve a place on a lean, stable, XFCE-based system?

---

### Post by Enno Borgsteede on 2011-11-16
Hi Steve,

I'm having similar problems as Fabian described on an old MSI based desktop PC (2003), running Xubuntu 11.10. The volume buttons have no effect at all, and when I press mute twice, sound doesn't come back until I unmute it with the mouse.

The reason that I write here is, that I'm not completely sure about what you mean. Should we file a bug report for Xubuntu because they put pulseaudio in there? Should I file a plea for the change you mention on the Xfce site?

The xfce4-settings-helper and xfce4-volumed are both installed on my system, which is a fresh Xubuntu 11.10 setup, but I haven't checked whether they are actually running. Is there a way to do that?

thanks for your help,

Enno

---

### Post by NickellossAych on 2011-12-13
I, too, am having the issue where the multimedia mute button successfully mutes the volume, but does not unmute.  I have an Envy 14.  I am also not familiar with all of these shell scripts and such.  What is the easy way to fix the issue?  Please ask for any information you need to help, thanks!

---

### Post by Xo-Mige on 2012-01-28
OK I figured this problem out and how to salve it with out any scripts or installing/removing anything. 

**the solution is to change to default sound card for xfce4 from the physical one to the pulse audio card**

to do that

go to xfce-menu->Settings->'Settings Editor' near the bottom

then find the 'xfce4-mixer' item on the right of the menu

then select  the active-card property and then edit it put this as the new value:

```
PlaybackInternalAudioAnalogStereoPulseAudioMixer
```

save it if it worked the effect should take place emmediatly

---

### Post by harry.bush on 2012-01-30
this worked for me... thanks!!

---

### Post by boblizar on 2012-03-10
just found this, your fix is not robotic enough for me.  still puzzling over it.

alt + f2

gnomoe-terminal

run

```

sudo su

```

```

cat > /etc/asound.conf << EOF
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
EOF
exit

```

(i think this requires restart to load this script)

bind ur mute key to this command

```

amixer sset Master toggle

```


bind ur + key to this command for 6 sound settings

```

amixer -c 0 set Master 2dB+

```

and your - key to this command for 6 sound settings

```

amixer -c 0 set Master 2dB-

```

bind ur + key to this command for 11 sound settings

```

amixer -c 0 set Master 1dB+

```

and your - key to this command for 11 sound settings

```

amixer -c 0 set Master 1dB-

```

---

### Post by false_chicken on 2012-03-28
> **Xo-Mige said:**
> OK I figured this problem out and how to salve it with out any scripts or installing/removing anything. 

**the solution is to change to default sound card for xfce4 from the physical one to the pulse audio card**

to do that

go to xfce-menu->Settings->'Settings Editor' near the bottom

then find the 'xfce4-mixer' item on the right of the menu

then select  the active-card property and then edit it put this as the new value:

```
PlaybackInternalAudioAnalogStereoPulseAudioMixer
```save it if it worked the effect should take place emmediatly

Works great! Thanks!

---

