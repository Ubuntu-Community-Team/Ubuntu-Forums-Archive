---
title: "fvwm + Mint 6 (Ubuntu 8.10) = no sound"
date: 2009-03-29
forum: Desktop Environments
---

### Post by k3ttc4r on 2009-03-29
Hey guys..

i got a little problem here - i'm using Mint 6 (based on Ubuntu 8.10) with fvwm. but i don't have sound.

with
```
AddToFunc StartFunction	
+ I Exec exec esd
```
in my .fvwm2rc, i got mpd to actually start playing, but i still don't hear anything.


on another note - my down-arrow key doesn't work, either..

thanks for your help!

---

### Post by jpkotta on 2009-03-29
PulseAudio has replaced esd.  Use
```
+ I Exec pulseaudio -D
```
It should be completely backward compatible with esd, and most Ubuntu packages offer the choice are now defaulted to PulseAudio.

You probably want to add
```

audio_output {
        type    "pulse"
        name    "PulseAudio"
}

```
to your mpdconf.

---

### Post by jpkotta on 2009-03-29
> on another note - my down-arrow key doesn't work, either..
Try running 
```
xev
```
and press your down arrow key.  You should see something like this:
```
KeyPress event, serial 29, synthetic NO, window 0x3000001,
    root 0x88, subw 0x0, time 3613002304, (596,521), root:(601,548),
    state 0x0, **keycode 104** (keysym 0xff54, **Down**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3000001,
    root 0x88, subw 0x0, time 3613002361, (596,521), root:(601,548),
    state 0x0, **keycode 104 **(keysym 0xff54, **Down**), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
If not, take whatever keycode is in the xev output (104 above) and run the command
```
xmodmap -e "keycode 104 = Down"
```

---

### Post by k3ttc4r on 2009-03-29
> **jpkotta said:**
> PulseAudio has replaced esd.  Use
```
+ I Exec pulseaudio -D
```
It should be completely backward compatible with esd, and most Ubuntu packages offer the choice are now defaulted to PulseAudio.

You probably want to add
```

audio_output {
        type    "pulse"
        name    "PulseAudio"
}

```
to your mpdconf.

i added pulse to my mpdconf a looong time ago :D 

and 
```
+ I Exec pulseaudio -d
```
didn't work either. solved it by putting
```
+ I Exec gnome-settings-daemon
```

probably not that elegant, but at least i can listen to some music now..


solved the problem with the down-arrow, too. the creator of the fvwm2rc mapped it to the left super key :D just removed that line, and everything's perfect again.

---

### Post by jpkotta on 2009-03-30
> **k3ttc4r said:**
> 
```
+ I Exec pulseaudio -d
```
didn't work either. solved it by putting


'-d' doesn't do anything except cause a syntax error.  It's case-sensitive.

---

