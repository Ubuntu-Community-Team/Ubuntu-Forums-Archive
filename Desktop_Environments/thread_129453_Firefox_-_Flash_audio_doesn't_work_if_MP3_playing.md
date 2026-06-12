---
title: "Firefox - Flash audio doesn't work if MP3 playing"
date: 2006-02-13
forum: Desktop Environments
---

### Post by sizzam on 2006-02-13
I know, I know, yet another audio thread...

Scenario:

Play Mp3 in Rhythmbox or XMMS - works fine.

While playing MP3, open up Frozen Bubble - works fine, I hear audio from both.

While playing MP3, open Firefox and go to webpage that contains a Flash animation with audio -  MP3 continues to play, but I get no audio from Flash.  If  I shutdown the MP3 player, I still get no audio from Flash.   If I close Firefox, reopen, and go to the page, I can then get audio from Flash.

If I go to a webpage with Flash audio in Firefox, I can hear the audio.  While that is playing, if I open up XMMS, I get "Please check that your soundcard is properly configured".  

I've tried a lot of sound fixes from the forums to correct this, so my settings may be a little screwy, but here are some details:

Breezy 2.6.12-10-k7
Firefox 1.5.0.1 (via Automatix)
Flash Player 7 (directly from Macromedia, not from repos)

/etc/esound/esd.conf
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d duplex
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

/etc/asound.conf
```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
```


/etc/libao.conf
```
default_driver=alsa
```


/etc/mozilla-firefox/mozilla-firefoxrc
```
FIREFOX_DSP="aoss"
```


gstreamer-properties
```
Default Sink:  ALSA
Default Source: ALSA

```


Please let me know if I can provide more information or if you have any suggestions.

---

### Post by bored2k on 2006-02-13
[http://www.ubuntuforums.org/showthread.php?t=75237&highlight=firefox+flash+sound](http://www.ubuntuforums.org/showthread.php?t=75237&highlight=firefox+flash+sound)

---

### Post by sizzam on 2006-02-13
I ran through those instructions prior to this post, same problem.   I have tried 

FIREFOX_DSP="aoss"
FIREFOX_DSP="none"
FIREFOX_DSP="auto"
FIREFOX_DSP="arts"

I can get sound from Flash with any of those settings, it just ties up my soundcard so I can't play anything else at the same time.

---

### Post by rfruth on 2006-02-13
Good tips 2k! however I too have trouble with Firefox (1.0.7) doing different things so I use two browsers, Fx is my workhorse & Mozilla Suite does streaming, flash and whatever if / when Fx is busy, this is what I did with Win XP way back when, then Mac OS X now with breezy ...

[ATTACH]6124[/ATTACH]

---

### Post by sizzam on 2006-02-13
I decided to wipe my drive and reinstall Ubuntu from scratch, and after I did I was able to resolve my problem on the version of Firefox that is native to Breezy 5.10 (Firefox 1.0.7).   Here are the steps I took to get it working:

First, after fresh install, I installed frozen-bubble
```

sudo apt-get install frozen-bubble

```

In gstreamer-properties, set both dropdowns to ALSA.

I was not able to get any audio from that game at this point.

```

sudo apt-get install libsdl1.2debian-all

```
(rebooted)

I was now able to get sound from frozen-bubble.

```

sudo apt-get install flashplayer-mozilla
sudo apt-get install alsa-oss

sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

```
(change from 'auto' to 'aoss')

Once I did that, I was able to play sound from Flash animations and also play MP3s in XMMS at the same time.

I don't know if this works in Firefox 1.5.0.7, I might just stay on 1.0.7 until Dapper goes stable.

---

### Post by sizzam on 2006-02-15
I upgraded to Firefox 1.5.0.7 via Automatix, and my sound problems with Flash returned.  If a Flash animation is playing audio, it ties up the soundcard.

This version of Firefox installed via Automatix does not seem to respect the setting in '/etc/mozilla-firefox/mozilla-firefoxrc'.

If I change my Firefox shortcut so that the launch command is 'aoss firefox %u',  then I have no sound issues.

---

### Post by RagingOcelot on 2006-02-17
[QUOTE=sizzam]I upgraded to Firefox 1.5.0.7 via Automatix, and my sound problems with Flash returned.  If a Flash animation is playing audio, it ties up the soundcard.

This version of Firefox installed via Automatix does not seem to respect the setting in '/etc/mozilla-firefox/mozilla-firefoxrc'.

If I change my Firefox shortcut so that the launch command is 'aoss firefox %u',  then I have no sound issues.[/QUOTE]

I also use the same command and can finally say that I have Flash and XMMS playing at the same time.  My Firefox 1.5 also seems to ignore the mozilla-firefoxrc file.  Does that command also open up the University of Arizona's homepage for you?

---

### Post by sizzam on 2006-02-18
[QUOTE=RagingOcelot]I also use the same command and can finally say that I have Flash and XMMS playing at the same time.  My Firefox 1.5 also seems to ignore the mozilla-firefoxrc file.  Does that command also open up the University of Arizona's homepage for you?[/QUOTE]

Ha, now that you mention it...  Firefox seems to launch correctly from a launcher using the command 'aoss firefox %u'.

However, if I put that in the configuration for 'gmail-notify', it opens up the Arizona homepage when I launch firefox from that app.   However, if I change the command to 'aoss firefox'  (without the %u), it doesn't do that anymore.

---

### Post by RagingOcelot on 2006-02-24
I upgraded to Firefox 1.5.0.1 and my sound setup is f'ed up again.  The "aoss firefox %u" command to open FF seemed to work before I upgraded.  Frozen Bubble's audio is working, but Firefox and XMMS audio doesn't work anymore.  Are your previous audio config files the same now after you installed that debian-all package?  I might just try and mimic your settings...

---

### Post by sizzam on 2006-02-24
[QUOTE=RagingOcelot]I upgraded to Firefox 1.5.0.1 and my sound setup is f'ed up again.  The "aoss firefox %u" command to open FF seemed to work before I upgraded.  Frozen Bubble's audio is working, but Firefox and XMMS audio doesn't work anymore.  Are your previous audio config files the same now after you installed that debian-all package?  I might just try and mimic your settings...[/QUOTE]

Yes, I actually didn't modify any of the default sound config files.  Here is essentially what I did in a nutshell:

sudo apt-get install libsdl1.2debian-all
sudo apt-get install alsa-oss

Run 'gstreamer-properties' and set both dropdowns to alsa.

In XMMS configuration, set the sound output to Alsa.

Put 'aoss ' in front of the command to launch Firefox.

Reboot (may or may not be necessary).

From that point, I was all set.

---

### Post by RagingOcelot on 2006-02-24
Ok, now I'm thoroughly confused.  Why does audio have to be so complicated?

I just edited my /etc/mozilla-firefox/mozilla-firefoxrc file to "esd" since that's what my sound system is configured for.  Then I changed XMMS to esd as well and now I can play FF, XMMS and Frozen Bubble audio all at the same time, if I so choose.  

Weird thing is, I'm still using the "aoss firefox %u" command to launch FF.  If I just use the standard "firefox" command, I get no Flash audio.  Strange.

---

