---
title: "Skype internal mic solution under Jaunty 9.04 Dell inspiron 1525"
date: 2009-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rubberist on 2009-05-05
Hope this helps a few people...

After a bit of a kerfuffle getting skype to work under Intrepid 8.10, you can imaginge how peeved I was for it to break again following the upgrade to Jaunty 9.04. Fear not,  I have got the internal mic working on my Dell inspiron 1525 under Ubuntu Jaunty 9.04 KDE 4.2 with no delay on the outgoing sound as follows:-

If you have a Dell inspirion or similar, set dell bios to alsa-base.conf:-

sudo gedit /etc/modprobe.d/alsa-base.conf
*
add to end
#dell amendment to make mic and headphone jacks work
options snd-hda-intel model=dell-bios

In Pulse Audio Manager - devices tab - hda intel source - properties - turn
volume up to 150% or so (not sure if this is absolutely necessary but it was one
of the early things I tried)...

Set up mic gain as follows:- (an amended alteration as described at:-
[https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html) thanks
to Marcus for this)

In order to make the micboost available to all pulseaudio clients in
Ubuntu, like gnome soundrecorder, you can also use the alsa softvol
trick, creating a new alsaboost device on top of which you will run pulseaudio,
by modifying the following files (1) and (2) below (make a backup of those files
first, just in case something breaks in your Ubuntu).

After restarting alsa/pulseaudio (or rebooting), you should verify that
the program "paman" shows alsaboost_source as the
default pulseaudio source. From now on, all ubuntu programs
that understand pulseaudio should be able to automatically benefit from
the micboost when recording. You can test this by changing the new +50dB
Mic slider in gnome volumecontrol while recording in gnome
soundrecorder. Let us know if other recording programs work fine as
well.

----
1) create/update your /etc/asound.conf:

sudo gedit /etc/asound.conf

Cut and paste the following into it:-

# creates a new alsaboost device that takes over sound card
pcm.alsaboost {
    type asym
    playback.pcm {
        type hw
        card 0
    }
    #software gain upto 50dB for digital microphone
    capture.pcm {
        type softvol
        slave.pcm "hw:0,0"
        control {
            name "+50dB Mic Capture Volume"
            card 0
        }
        max_dB 50.0
    }
}
ctl.alsaboost {
  type hw
  card 0
}

----
2) modify your /etc/pulse/default.pa, in order to add the two uncommented lines
below at a similar place in your default.pa (around line 35 in my case), and keeping all
the remaining lines in your default.pa (this location is important, do not put them
at the bottom of default.pa or otherwise alsaboost will not load properly in pulseaudio
because it will prefer to load, instead, the original sound device via module-hal-detect a
few lines down):

sudo gedit /etc/pulse/default.pa

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0

load-module module-alsa-source device=alsaboost source_name=alsaboost_source
# load-module module-alsa-sink device=alsaboost sink_name=alsaboost_sink

#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=inp$
#load-module module-null-sink 
#load-module module-pipe-sink


2b) in case you have several devices, or for some other reason alsaboost doesn't
become the default source/sink in pulseaudio, you can force that by adding the
following two lines at the bottom of default.pa:

# set-default-sink alsaboost_sink
set-default-source alsaboost_source

(you can set the sink to alsaboost as the default too by uncommenting the 2 sink lines if you wish)

----
In your volume control mixer you should have a new slider +50db gain. Nudge it up from half way to three quarters on.

In skype set sound out and ringing to pulse, sound in to alsaboost

caveat 1: skype doesn't like to use pulseaudio, so you should still
choose the "alsaboost" device for its SoundIn configuration, but you can
use "pulse" for its SoundOut and Ringing. This seems to be a deficiency
in skype, and the side-effect is that while skype is in a call, you
won't be able to use the mic in a different application like gnome's
soundrecorder. Also, if another program is using the mic, skype won't be
able to use it.

caveat 2: under this configuration, skype also likes to mess with the
value of the +50dB Mic slider if the option "Allow skype to
automatically ajudst my mixer levels" is checked in. I would recommend
disabling this option, or at least keeping in mind that if the mic stops
recording, it's very likely that skype messed with the micboost slider.

Skype should now work again...

---

