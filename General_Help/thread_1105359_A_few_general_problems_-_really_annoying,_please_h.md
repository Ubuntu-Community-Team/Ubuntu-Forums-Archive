---
title: "A few general problems - really annoying, please help!"
date: 2009-03-24
forum: General Help
---

### Post by Letterbomb05 on 2009-03-24
Hi, a few problems that are really annoying right now...

[COLOR="SeaGreen"]**_[Solved]Problem 1:_**[/COLOR]
On startup, I only have a black screen with white text; no GUI. It asks me for my username & password, and then pretty much just gives me the terminal. I then have to type startx to get onto my desktop. How can I fix this and have it so that I can login through my normal splash page? 
[COLOR="SeaGreen"]
**_[Solved]Problem 2:_**[/COLOR]
I've lost my little icon in the top right hand corner of the screen; I now have to shut down using an alternative through system. This is quite annoying. Screenshot:
 [[IMG]http://img19.imageshack.us/img19/7338/exampleg.png[/IMG]](http://img19.imageshack.us/my.php?image=exampleg.png)

Is there any way that I can get this back? :(
[COLOR="Red"]
**_[Unsolved]Problem 3:_**[/COLOR]
PHPMyAdmin:- I have installed xampp and PHP5 with mysql etc. I then installed phpmyadmin and yet when I try to access localhost/phpmyadmin; I simply get a 404 error. :/ If anyone knows how to get this working please post!

[COLOR="SeaGreen"]
**_[Solved]Problem 4:_**[/COLOR]
I DID have sound working; however now it has randomly stopped working. When I try to alter volume level or such, I simply get a popup box saying: "No volume control GStreamer plugins and/or devices found."


Sorry, I'm still new to Linux, however thanks for reading; If anyone has any questions about any of the problems, please ask :)

---

### Post by fcuk112 on 2009-03-24
i think this would resolve your 2nd problem:

```

cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity 

```

---

### Post by rockstone on 2009-03-24
Resting gnome settings to defaults is a bit drastic. To get back the shut down icon just right click the panel > add to panel, and add the shut down button. 

For the first problem maybe check what your login screen is set to in system > administration > login window.

---

### Post by oldos2er on 2009-03-24
To enable GDM, run
```
sudo /etc/init.d/gdm start
```
after you login. Then go to System, Administration, Login window, Local to make a permanent change.

---

### Post by mithbuntu on 2009-03-26
I have the same login/no sound/no user panel problem after extensive trouble shooting to get my nvidia sli cards to work (check my previous thread).  I honestly think some packages need to be removed and reinstalled for this solution, but I don't know which.

I've tried reinstalling gdm, but that didn't work.

> **oldos2er said:**
> To enable GDM, run
```
sudo /etc/init.d/gdm start
```
after you login. Then go to System, Administration, Login window, Local to make a permanent change.

Starting GDM with this problem does not do anything.  It says "Starting Gnome Desktop Manager ...        [ok]" then you are dumped back to the terminal.  The only way to get back in is typing "startx" weither GDM is running or not.

Going to the login window panel with this problem does not seem to do much.  Once you've typed startx, GDM doesn't even seem to indicate a problem.  I am curious though.  On the security tab>configure x server>servers to start list: should there only be one: XGL?  I did some fiddling around with XGL to try and get compiz working, and I'm not sure if that's the default.  

My startup command is "/usr/X11R6/bin/X -br -audit 0 "


As for the sound problem perhaps the problem lies in .xsession-errors ? Here's a snip of mine relating to audio:
```

Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] Failed to connect to server: Invalid argument
[AO_ALSA] alsa-lib: pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[AO_ALSA] Unable to set hw-parameters: Input/output error
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Permission denied
[AO_ALSA] alsa-lib: pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[AO_ALSA] Unable to set hw-parameters: Input/output error
mcop warning: user defined signal handler found for SIG_PIPE, overriding
ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
DBus connection has been lost, trackerd will now shutdown
Xsession: X session started for drew at Thu Mar 26 01:08:48 MDT 2009
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: another SSH agent is running at: /tmp/ssh-XjbxGy9196/agent.9196
Window manager warning: Failed to read saved session file /home/drew/.config/metacity/sessions/10e88e3a4a9b4f0496123805132839225700000091960009.ms: Failed to open file '/home/drew/.config/metacity/sessions/10e88e3a4a9b4f0496123805132839225700000091960009.ms': No such file or directory
ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

Failed to play sound: IO error

```

---

### Post by mithbuntu on 2009-03-26
How'd the OP resolve 1,2 and 4? OP never posts what worked.

---

