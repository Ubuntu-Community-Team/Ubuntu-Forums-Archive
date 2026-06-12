---
title: "nvidia twinview easy switching 2nd monitor with TV on the fly"
date: 2007-11-17
forum: Desktop Environments
---

### Post by BlackShift on 2007-11-17
Hi,

Summary: I'm looking for an easy way to switch which monitor is used as the 2nd monitor with twinview (switching between my CRT to my TV).

I've got an GeForce 5700, with a DVI,VGA and TV out connectors, all three connected to respectively a DFP (tft), a CRT and a TV. I figured I can only use two at the same time (hardware limitation?), so I decided I'd like to use either the DFP and the CRT, or the DFP and the TV together.

So far it works 'good enough'. The default setup is DFP+CRT in twinview (with compiz etc, everything works, fresh install). I can use nvidia-settings to exchange the CRT for the TV by:
[LIST]
[*]disabling the CRT
[*]enabling the TV
[*]positioning the TV to match where the CRT was
[/LIST]
and the other way around to get the CRT back. Since I've got this to work without having to restart X etc., I thought it should be possible to do it much easier, with just a view clicks/keystrokes but I can't figure it out.

I think this should be possible to do with different metamodes. I can start X with the DFP and either the CRT or the TV by one of these lines:
```
    Option         "metamodes" "DFP: 1680x1050 +0+0, CRT: 1024x768 +1680+150, TV: NULL" # DFP + CRT
    Option         "metamodes" "DFP: 1680x1050 +0+0, TV: 800x600 +1680+0" # DFP + TV
```
But combining these only allows the DFP and the CRT to be used (in either resolution):
```
    Option         "metamodes" " DFP: 1680x1050 +0+0, TV: 800x600 +1680+0; DFP: 1680x1050 +0+0, CRT: 1024x768 +1680+150"
```

Another thing I looked at was trying to script this. There is an nvidia-settings command line interface, but I cannot figure out how to change the twinview settings with it. By now I'm so skilled in switching monitors that I thought about writing a mouse moving macro of some sort, but that seems to be a very big hack :-). Any ideas?

---

### Post by Kzin on 2008-03-25
I'd like to give this older post a nice big bump.  I am trying to do a little toolbar app to do the same thing... I am a pro at swapping the modes, but it has to be something that can be done.

I have pretty much the same setup, shy of the CRT (Have 2 DFP).

So, I started by looking at what the "Apply" button does, to do this, I started nvidia-settings as such;

```
gksudo 'nvidia-settings --verbose=all'
```

When I enabled the TV, I got...
```
  Setting display device 'ViewSonic VX922' as Off for MetaMode 0 on Screen
  0.  (There are already two active display devices for this MetaMode.
```

Then when I pressed Apply....
```
Updating Screen 0's MetaModes:
  Added   > TV-0: nvidia-auto-select @1024x768 +1280+0, DFP-0: 1280x1024
  @1280x1024 +0+0, DFP-1: NULL
  Current mode: 2560x1024 (id: 50)
  Switching to mode: 3584x1024 (id: 51)...
  Using   > TV-0: nvidia-auto-select @1024x768 +2560+0, DFP-0: 1280x1024
  @1280x1024 +0+0, DFP-1: NULL
  Removed > DFP-0: 1280x1024 @1280x1024 +0+0, DFP-1: nvidia-auto-select
  @1280x1024 +1280+0, TV-0: NULL
  Moved   > TV-0: nvidia-auto-select @1024x768 +2560+0, DFP-0: 1280x1024
  @1280x1024 +0+0, DFP-1: NULL
  Moved   > TV-0: nvidia-auto-select @1024x768 +1280+0, DFP-0: 1280x1024
  @1280x1024 +0+0, DFP-1: NULL
```

So, does anyone know about switching metamodes on the fly?  nvidia-settings can do it, we should be able to do it somehow too.  Anyone recognize this output?  Point me in the right direction?

---

### Post by Kzin on 2008-03-25
Ooo, found something that should help track this down, so we can see what nvidia-settings is really doing...

[nvidia-settings Source Code]("ftp://download.nvidia.com/XFree86/nvidia-settings/")

---

### Post by Kzin on 2008-03-25
OK, since this is about to get code intensive, I created a new thread [here.]("http://ubuntuforums.org/showthread.php?t=735492")

---

