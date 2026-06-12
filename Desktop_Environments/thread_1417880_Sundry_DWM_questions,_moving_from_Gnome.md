---
title: "Sundry DWM questions, moving from Gnome"
date: 2010-02-27
forum: Desktop Environments
---

### Post by 655 on 2010-02-27
Some of the threads on dwm are too old to post to, so I started a new thread.  
I'm sure some of you have experience going from Gnome down to a plain x session with dwm.

I have a few issues that would formerly have been handled automatically in a Gnome session, but I need to set them up by hand and am unsure how.

[B]1. Wifi management
2. Sound card
3. SCIM/XIM IME[/B]

1. This was formerly being handled by nm-applet.  I switched to wicd and the problem was solved.
2. Pulseaudio and/or amixer do not appear to be starting by default.  I don't know where Ubuntu/Gnome are handling this on a per-session basis, but this works in a Gnome session with the volume control applet.  I tried launching amixer or pulseaudio as daemons in my .xinitrc, but they throw errors.
3. XIM is a *big* headscratcher.  Again, this works in a regular Gnome session.  I use scim-anthy and can call up the toolbar at a keystroke.  Launching scim -d through xinit succeeds in running it as a daemon, but the keystrokes don't do anything.  The panel appears to be geared towards GTK environment.

In any case, there is less automation going on at startup, evidently.  I'm launching X with startx and a few programs and dwm.  If I use a Gnome session with dwm as the WM all of the above work without incident.

See below on pastebin:
[Startx log]("http://ubuntu.pastebin.com/gbRddEnd")
[Startx log when using pulseaudio -D]("http://paste.ubuntu.com/385462/")
[Xinit]("http://ubuntu.pastebin.com/DvQG6GD2")

Thoughts??

---

### Post by falconindy on 2010-02-27
If you're committed to using DWM, I'd highly recommend ditching Pulse. It's horrible and you should avoid it if you can. The error you're receiving is because it's not being called as root.

amixer isn't a daemon and just gets invoked to do its job and then dies. I've got the following lines in my config.h:

```
static const char *volup[] = { "amixer", "-q", "set", "PCM", "5+" };
static const char *voldown[] = { "amixer", "-q", "set", "PCM", "5-" };
```
and then they're bound to mod4+z/x further down...

```
     { MODKEY,                       XK_x,      spawn,          {.v = volup } },
     { MODKEY,                       XK_z,      spawn,          {.v = voldown } },
```

Honestly, I'm not sure what to do about SCIM. There was a similar thread on the Arch forums not too long ago, but I don't recall the outcome.

Also, feel free to nose around my GitHub repos (link in my sig). I've got my DWM configs, my ~/bin and dotfiles all maintained there. DWM is fun =)

---

### Post by 655 on 2010-02-27
Okay, I wasn't thrilled about pulse anyway.  But FWIW it didn't run as root either for some reason.

I'm going to try your amixer configs.  My xinit is posted above in a pastebin.
SCIM is a huge sticking point for me because I need CJK input on a daily basis.

And I enabled sigs just so I could see your links.  How big of me.

---

### Post by 655 on 2010-02-27
;I noticed that on your git hub you had *volup and *voldown calling something called volOSD, not amixer.  Regardless, I tried setting it to amixer, but no luck.

As a test, I tried launching some mp3s with mplayer from the command line; it hangs with 
```
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Permission denied
```:-( I don't know much about ALSA but this puzzles me.  Evidently the default Gnome session is handling permissions to open the ALSA socket or whatever differently.

Interestingly, I can only open alsamixer or ALSA as root (sudo). Wth is going on?

---

### Post by 655 on 2010-02-27
Added self to group audio

ls -l /dev/snd

crw-rw----+ 1 root audio 116, 7 2010-02-27 10:53 controlC0
crw-rw----+ 1 root audio 116, 6 2010-02-27 22:45 pcmC0D0c
crw-rw----+ 1 root audio 116, 5 2010-02-27 22:45 pcmC0D0p
crw-rw----+ 1 root audio 116, 4 2010-02-27 10:53 pcmC0D1p
crw-rw----+ 1 root audio 116, 3 2010-02-27 10:53 seq
crw-rw----+ 1 root audio 116, 2 2010-02-27 10:53 timer

but no change in above-mentioned behavior.

---

### Post by falconindy on 2010-02-27
It's probably consolekit handling permissions transparently when you're in Gnome. Are you a member of the 'audio' group? Perhaps you could try launching dwm through your dwm-startup script as:
```
exec ck-launch-session /usr/bin/dwm
```

I didn't mention the volOSD script because i didn't want to add more (possible) candidates for issues. If you want, you'll find that script in my "bin" repo. It's a fancy wrapper for notify-osd and notify-send so I get a popup whenever I change my volume. Probably one of the only "pretty" things I have on my desktop.

edit: you beat me to the audio group mention! You'll have to log out for that change to take effect, though,.

---

### Post by 655 on 2010-02-28
PMed you so we can discuss off-thread.
Edit: nevermind, you aren't accepting PMs.  Please PM me so I can give you my e-mail, as this is branching out into a series of questions and I don't want to spam the board.

---

### Post by 655 on 2010-03-05
Wasn't able to get ahold of you off-thread, so here goes some more:

Changing permissions to allow me in the audio group worked, and then I noticed that sundry audio files (mp3s, movies) were playing, but not embedded flash video.  After doing the consolekit part, that worked as well.

What suite of apps does consolekit control?

Also, for some reason your key bindings for increasing and decreasing volume don't seem to do anything (not the volOSD script ones).  I looked in the log and alsamixer didn't seem to think those were valid commands, because it was printing the help text.

I've noticed that when I start a new session, alsamixer is always set to the lowest volume and I have to manually increase.  Is there some way to change and tick a flag so that it starts at a regular level?

Still very stuck on the SCIM issue, which prevents full-time use of DWM, and I find myself having to drop into Gnome.

---

### Post by falconindy on 2010-03-05
> **655 said:**
> Changing permissions to allow me in the audio group worked, and then I noticed that sundry audio files (mp3s, movies) were playing, but not embedded flash video.  After doing the consolekit part, that worked as well.

What suite of apps does consolekit control?
ConsoleKit is an abstraction layer that allows a user at the console to do various things that would otherwise require elevated permissions. Personally, I skip out on ConsoleKit and just allow myself what I need through group permissions and udev rules.

> **655 said:**
> Also, for some reason your key bindings for increasing and decreasing volume don't seem to do anything (not the volOSD script ones).  I looked in the log and alsamixer didn't seem to think those were valid commands, because it was printing the help text.
That's... odd... did you copy and paste my lines verbatim? Try adding 'NULL' as a final field.

> **655 said:**
> I've noticed that when I start a new session, alsamixer is always set to the lowest volume and I have to manually increase.  Is there some way to change and tick a flag so that it starts at a regular level?
If you look in the init.d script for ALSA, you'll see it setting volume levels to zero on shutdown, and restoring them on startup. You can set the default levels by going into alsamixer and settings how you like, then issuing "sudo alsactl store", but I've heard that this doesn't work for some people (oddball errors). The other option is to just prevent ALSA from muting the volume levels on shutdown by commenting out that line in the init.d script.

QUOTE=655;8923617]Still very stuck on the SCIM issue, which prevents full-time use of DWM, and I find myself having to drop into Gnome.[/QUOTE]
I'd like to help, but as I'm just an arrogant American, I know nothing about SCIM. Perhaps you should try the dwm@suckless mailing list.

---

### Post by 655 on 2010-03-07
> ConsoleKit is an abstraction layer that allows a user at the console to do various things that would otherwise require elevated permissions. Personally, I skip out on ConsoleKit and just allow myself what I need through group permissions and udev rules.Thank you.

> That's... odd... did you copy and paste my lines verbatim? Try adding 'NULL' as a final field.NULL did the trick.  I checked by using the hotkeys inside of alsamixer and only appending NULL generated a response.  I changed the line to control Master instead of PCM, which is a lame way of getting around the ALSA volume levels resetting themselves, because I found that, as you mentioned, it is finicky.  alsactl store was finicky, so this brute-force method will work.  PCM doesn't change anyway.

> 
I'd like to help, but as I'm just an arrogant American, I know nothing about SCIM. Perhaps you should try the dwm@suckless mailing list.Yeah, I need to get on that...

Thanks friend!

---

### Post by 655 on 2010-03-08
*Pats self on back

I basically fixed SCIM startup!  By actually bothering to read the man page (blush), I learned that you have to export xim/scim as your GTK and QT module BEFORE you start an X session, otherwise you have to do it in the terminal before starting your apps.  

What I was doing was exporting those things in my init script at the same time I launched the terminal, so scim wouldn't load unless I started a new terminal emulator and opened apps from there.  In other words, the module is applied to all subsequently opened apps from that terminal session, but since my first terminal session tried to export simultaneously, I couldn't get the IME to respond until launching another terminal from *that* session.  Since I never open more than one instance (use screen), I was blissfully unaware of this.

I realized I need to put the strings about exporting those modules in my bash_profile or bash_rc so that they execute on login before I start X.  I did that and it works a dream.

The only thing is, it spits this out
```
bash: export: `$': not a valid identifier
```but everything runs OK.  Is there some kind of special syntax I need to observe in the bashrc or profile file?  I just slapped this in there:
```
export LANG="en_US.UTF-8"
XMODIFIERS="@im=SCIM"
export XMODIFIERS
GTK_IM_MODULE="xim"
export GTK_IM_MODULE
QT_IM_MODULE="xim"
export QT_IM_MODULE
```

---

