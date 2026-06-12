---
title: "Can't get sound to come out of the earphones"
date: 2009-04-20
forum: General Help
---

### Post by Jammanuser on 2009-04-20
[COLOR="Red"][SIZE="5"](Note: This problem has been solved; see [post=7116686]post #38[/post] for resolution)[/SIZE][/COLOR]
I'm running Ubuntu 8.10, and I can't get sound to come out of my earphones, which I plug into the earphone jack, but the sound comes out fine (though a bit quiet compared to Windows) out of the built-in speakers. How do I get my earphones to work in Ubuntu (its turned up to max and I can't hear a thing)?
I have a Dell Studio 1535 laptop.

Thanks in advance.

-Jam man

:guitar:

---

### Post by vernonrj on 2009-04-20
Does this help?

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I had this sound problem and I fixed it by going through this article.

---

### Post by Jammanuser on 2009-04-20
Thanks. :)
I'm following that howto now, and I'll let you know if it solves the problem or not.

---

### Post by Jammanuser on 2009-04-20
Ok, I followed the Interpid instructions all the way to the end, but my earphones are still not working in Ubuntu.

Here is the listing of my sound devices:

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The application I am trying to use, which wont play any sound through the earphones is Totem Movie Player, and it does indeed show up in the Playback tab of the Volume Control of PulseAudio Applet, with the volume turned up to max, but I still can't hear a thing with the earphones plugged in, and my sound mixer turned up all the way as well. 

Any other ideas?

Thanks

---

### Post by Jammanuser on 2009-04-20
Here is the verbose output from pulseaudio on my system:

```
$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa28_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa28_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```
It hangs at that last part in the Terminal, and doesn't complete.

---

### Post by vernonrj on 2009-04-20
I might have an idea. In Ubuntu, sometimes there is a separate channel titled "Headphone" after you go through this tutorial. On my machine, this channel is under HDA Intel (Alsa Mixer). Sometimes it is not visible, so check the "preferences" to see if it's hidden.

*edit: if you have the command, "amixer" installed, try that.*

---

### Post by Jammanuser on 2009-04-20
> **vernonrj said:**
> I might have an idea. In Ubuntu, sometimes there is a separate channel titled "Headphone" after you go through this tutorial. On my machine, this channel is under HDA Intel (Alsa Mixer). Sometimes it is not visible, so check the "preferences" to see if it's hidden.

Unfortunately, I cannot find it...:(
Where is it exactly?

---

### Post by Jammanuser on 2009-04-20
Here's the output of "amixer":

> $ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]


---

### Post by vernonrj on 2009-04-21
Hmm... okay. This should do it. 

[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by sharon.gmc on 2009-04-21
I solved my problem because of this. Thank you!

---

### Post by vernonrj on 2009-04-21
Glad to be of help.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> Hmm... okay. This should do it. 

[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
It says in that post to add a line to the "alsabase" file called
> options snd-hda-intel model=*modelname*
where "modelname" is replaced with the actual name, of course, and it tells me to run the commands "aplay -l" and "cat /proc/asound/card0/codec#* | grep Codec", but the trouble is I'm not sure which one produces the model name. :P The former produces the output already posted of course, but the second outputs the name of my codec, but I'm not sure if that's what I'm supposed to replace "modelname" with or not...?
The "aplay -l" produced something in the output that may be considered the model name, i.e. something called "STAC92xx", but though there's a list of model names in that post beginning with "STAC92", I'm not sure which one I'm supposed to use, and I can't find my actual laptop model (i.e. the Dell Studio 1535) mentioned there. So how can I tell which one to use? The "xx" part of the model name (if that's what it is) does not help me very much...
Additionally, am I supposed to add the name of the codec (more specifically "IDT 92HD73C1X5") to the end of the model name, and if not, why have me run that command in the first place if I'm not supposed to use it for this purpose?

---

### Post by vernonrj on 2009-04-21
umm... As far as I know, it's pretty generic. I run a Sony Vaio, so in my config, *modelname* is replaced with *vaio*. Yours should just be *dell*.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> umm... As far as I know, it's pretty generic. I run a Sony Vaio, so in my config, *modelname* is replaced with *vaio*. Yours should just be *dell*.
Ok, well that's what I thought originally, but after I looked through that list, it threw me off because it appeared to have specific "model names" for the soundcards, but if its just the brand name that I'm supposed to put in there, then ok...
So this should do it then? My earphones should work after this (after saving that line to the file)?

---

### Post by vernonrj on 2009-04-21
yeah, you should be able to just log out and log back in, and have it working. If it's not, make sure you check that headphone thing I mentioned earlier.

---

### Post by Jammanuser on 2009-04-21
Nope. :(
It didn't work. 
I logged off, and logged back on, but the earphones still don't work.
Should have known it wouldn't have been this easy...

---

### Post by vernonrj on 2009-04-21
I checked through some posts about your laptop model, and found this page

[http://ubuntuforums.org/showthread.php?t=966241](http://ubuntuforums.org/showthread.php?t=966241)

Some people had luck with turning up the "surround" channel. Did any new channels appear with the new configuration?

[i]edit: you could also try checking through here:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)[/i]

[i]edit 2: try using dell-m6 instead of just dell.
reference: [http://ubuntuforums.org/showthread.php?t=966241&page=4](http://ubuntuforums.org/showthread.php?t=966241&page=4)[/i]

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> I checked through some posts about your laptop model, and found this page

[http://ubuntuforums.org/showthread.php?t=966241](http://ubuntuforums.org/showthread.php?t=966241)

Some people had luck with turning up the "surround" channel. Did any new channels appear with the new configuration?

[i]edit: you could also try checking through here:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)[/i]
Ok, thanks for those links. Haven't had time to go over them in detail yet (especially the one on the AlSA upgrade script), but they look very useful. Based on the info in the first link, I played around a little with the options you get to after double-clicking on the sound icon on the taskbar. I learned my Surround sound option was not selected (so I selected it), and it was muted (so I unmuted it), though it was turned up to max already by default. I also played around with other options too, but nothing I've tried has worked yet. :( The headphone volume is up plenty, I tried different "Devices" (the default was the HDA Intel (Also Mixer) that you mentioned in an earlier post), one of them the HDA ATI HDMI device. I tried ticking the option called "Headphone as line out" (don't know if needs to be selected or not for the headphones, but it seems likely that it does; the default was unselected). But still nothing works, though I have not tried logging off, and logging on again after doing all of that (will try it now though).

Thanks for your help.

---

### Post by vernonrj on 2009-04-21
If the "dell-m6" doesn't work, there are a lot of other ones for different dell configurations on this page:

[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

I added this earlier, but I felt it would be good to put it up again. I can't specifically find a "dell studio" model in there, but you might have more luck than me.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> 

[i]edit 2: try using dell-m6 instead of just dell.
reference: [http://ubuntuforums.org/showthread.php?t=966241&page=4](http://ubuntuforums.org/showthread.php?t=966241&page=4)[/i]
It didn't help. Its still not working.
Anyway, I think I'm going to bed, and will work on this problem more tomorrow. I'm getting to tired to focus on the problem, and think clearly. 
Thanks for all the help so far, btw.

Good night.

EDIT: Besides...isn't the "Dell-m6" for Dell desktops, according to that link you posted? I'm running a laptop.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> If the "dell-m6" doesn't work, there are a lot of other ones for different dell configurations on this page:

[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

I added this earlier, but I felt it would be good to put it up again. **I can't specifically find a "dell studio" model in there, but you might have more luck than me.**
There's not one. I already looked through it, and it only mentioned the XPS, and Inspiron laptop product lines. Not Studio. There could be a model though that has the same soundcard, I suppose...I don't know. I will have to look into it tomorrow, and see.

---

### Post by vernonrj on 2009-04-21
yes, dell-m6 is for desktops, but I was looking through some pages and that kept popping up... thought it was worth a shot.
here's another link
[http://www.linlap.com/wiki/dell+studio+15](http://www.linlap.com/wiki/dell+studio+15)

Also, using this reference
[http://guide.ubuntuforums.org/showthread.php?t=1110204](http://guide.ubuntuforums.org/showthread.php?t=1110204)

I found another possible model...
snd-hda-intel model=ref

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> yes, dell-m6 is for desktops, but I was looking through some pages and that kept popping up... thought it was worth a shot.
here's another link
[http://www.linlap.com/wiki/dell+studio+15](http://www.linlap.com/wiki/dell+studio+15)

Hmm...according to that, the "Headset sound (both side jacks), external mic and speaker sound, to function properly in terms of appropriate muting and unmuting requires an alsa version more recent than 1.0.18a." So how do I check which alsa version I have currently? Maybe its not recent enough.

---

### Post by vernonrj on 2009-04-21
you can type "alsamixer" on terminal.
[i]edit: I also read on this forum that you can get sound working through the package "gnome-alsamixer".
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/51862](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/51862)

edit2: specifically marcobra's post[/i]

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> you can type "alsamixer" on terminal.
[i]edit: I also read on this forum that you can get sound working through the package "gnome-alsamixer".
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/51862](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/51862)

edit2: specifically marcobra's post[/i]
Thanks for that. I believe my problem is close to being fixed. I followed marcobra's suggestions, and ran the commands
```
sudo killall pulseaudio
sudo alsa force-reload
```
and then went and changed all of the things in System>Preferences>Sound to Alsa. One thing I was not sure of which one to use as my "Default Mixer Tracks" device. I have two that mentions "Alsa", one of them "HDA ATI HDMI (Alsa mixer)" and the other one "HDA Intel (Alsa mixer)". I tried both, but my earphones are still not working. 
I used "alsamixer" which opened up a terminal application, but I checked all that, and the volume appears to be up in every channel, and nothing appears to be muted.
The output of "sudo alsa force-reload" was:
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gorilla/.gvfs
      Output information may be incomplete.
Terminating processes: 5881lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gorilla/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gorilla/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gorilla/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-seq snd-pcm-oss snd-mixer-oss snd-seq-device snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-seq snd-pcm-oss snd-mixer-oss snd-seq-device snd-pcm snd-timer snd-page-alloc.
The version of alsamixer that I have is 1.0.17, so it seems I may have to update it to something more recent, but I'm not sure how do that.

Do I just run:
```
sudo apt-get install alsa
```
or 
```
sudo apt-get install alsamixer
```
? And this will install the latest version?

Thanks very much.

EDIT: That didn't work...
I just tried it, and it said "alsa-base" was the newest version when I ran the first command, and then when I tried "sudo apt-get install alsamixer", it said no such package. So I tried "sudo apt-get install alsa-base" instead, and it said the same thing as the first command, i.e. I already have the newest version.

---

### Post by michy99 on 2009-04-21
Sorry if this sounds like a stupid and obvious question, but have you tested the headphones themselves to make sure they work?

---

### Post by vernonrj on 2009-04-21
Ha, I was on Arch when I checked that; it's 1.0.19 in Arch, it's 1.0.17 in Ubuntu. Anyway, that Dell laptop has two cards, so it's possible Ubuntu is setting the wrong one as default. I believe the HDA intel is the one that should be set. Hmm... You could probably build the newest Alsa version from source. Also, did you do the system-wide equalizer part, too? If you did, you should try reverting that.

---

### Post by qualityfirstac on 2009-04-21
hmmmmmmm indeed

[http://www.qualityfirstac.com](http://www.qualityfirstac.com)

---

### Post by Jammanuser on 2009-04-21
> **michy99 said:**
> Sorry if this sounds like a stupid and obvious question, but have you tested the headphones themselves to make sure they work?
Haha. :D Yes, the same earphones I'm trying on Ubuntu works perfectly fine from either XP or Vista (my other two main OSes on the same computer). It is only in Ubuntu that they don't work.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> Ha, I was on Arch when I checked that; it's 1.0.19 in Arch, it's 1.0.17 in Ubuntu. Anyway, that Dell laptop has two cards, so it's possible Ubuntu is setting the wrong one as default. I believe the HDA intel is the one that should be set. Hmm... You could probably build the newest Alsa version from source. Also, did you do the system-wide equalizer part, too? If you did, you should try reverting that.
Sorry, I'm not sure what you mean by "system-wide equalizer part". Would you mind explaining? Thanks. BTW, I probably tried just about all the different combinations of options that I could think of, but I still could not get it to work. I will keep trying though...

---

### Post by Jammanuser on 2009-04-21
> **qualityfirstac said:**
> hmmmmmmm indeed

[http://www.qualityfirstac.com](http://www.qualityfirstac.com)
Nice! :D Air-conditioning! Are you trying to suggest I need some fresh air? ;)

---

### Post by vernonrj on 2009-04-21
Well, in this article, posted earlier,

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

it has an option for a system-wide equalizer after the pulseaudio fixes, and I was wondering if you had gone through that too. I was going to say that you should try reverting that if you did.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> Well, in this article, posted earlier,

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

it has an option for a system-wide equalizer after the pulseaudio fixes, and I was wondering if you had gone through that too. I was going to say that you should try reverting that if you did.
Aaaaah, I see. No, I did not follow that part of the guide, just the instructions for PulseAudio for Intrepid. So I shouldn't have to revert that.

---

### Post by vernonrj on 2009-04-21
Found something else that may or may not help you.

[http://forums.opensuse.org/hardware/laptop/392178-opensuse-11-dell-studio-1535-a.html](http://forums.opensuse.org/hardware/laptop/392178-opensuse-11-dell-studio-1535-a.html)

[http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html](http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html)

I'm running out of ideas. Reviewing, neither of the headphone jacks work? You didn't get errors going through the pulseaudio guide? you tried both model=dell-m6 and model=ref? (I know it says dell-m6 is desktop, but I just want to make sure that doesn't work) You've restarted your computer lately to make sure this stuff isn't working?

If all this still isn't helping, I noticed there is a "Dell Ubuntu Support" in the Main support categories. Someone there may have more luck.

[i]edit: found something else: type this code into the terminal:
```
head -n 1 /proc/asound/card0/codec*
```
This should tell you the codec for your card, and you can use it to narrow down the list on
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
(one of the dell model names might work for the studio)[/i]

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> Found something else that may or may not help you.

[http://forums.opensuse.org/hardware/laptop/392178-opensuse-11-dell-studio-1535-a.html](http://forums.opensuse.org/hardware/laptop/392178-opensuse-11-dell-studio-1535-a.html)

[http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html](http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html)

I'm running out of ideas. Reviewing, neither of the headphone jacks work? You didn't get errors going through the pulseaudio guide? you tried both model=dell-m6 and model=ref? (I know it says dell-m6 is desktop, but I just want to make sure that doesn't work) You've restarted your computer lately to make sure this stuff isn't working?

If all this still isn't helping, I noticed there is a "Dell Ubuntu Support" in the Main support categories. Someone there may have more luck.

Thanks for the last two links. They look really useful. 
In answer to your questions, yes, I have tried both "model=dell-m6" and "model=ref" (though I have not tried "model=dell-m6" yet with the latest suggestions; it was set to "ref" when I tried the last suggestions). And no, there were no errors beyond normal when I was going through the pulseaudio guide. Some of the things (that the guide wanted me to remove) though were not installed, so I got relative messages (i.e. errors of some sort) in the output, but that is of course to be expected. As for whether or not I restarted, no, I did not. It was late last night when I was doing most of that stuff, and so I just went to bed after finally turning off the computer. And then when I tried the suggestions in the launchpad.net page, it was this morning, and I have been doing other stuff on the computer until now. So no, I have not restarted any to test it. 
> 
[i]edit: found something else: type this code into the terminal:
```
head -n 1 /proc/asound/card0/codec*
```
This should tell you the codec for your card, and you can use it to narrow down the list on
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
(one of the dell model names might work for the studio)[/i]
Thanks. I will let you know how it goes.

---

### Post by Jammanuser on 2009-04-21
> **vernonrj said:**
> 
[i]edit: found something else: type this code into the terminal:
```
head -n 1 /proc/asound/card0/codec*
```
This should tell you the codec for your card, and you can use it to narrow down the list on
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
(one of the dell model names might work for the studio)[/i]
Ok, my codec is
> IDT 92HD73C1X5
So based on the list in that post, the model names under 
> STAC92HD73*
namely
> 
ref		Reference board
dell-m6	        Dell desktops

which is of course what I already tried, and it didn't work. I just tried the dell-m6 option with all the selected things turned to ALSA in System>Preferences>Sound like mentioned in that launchpad page, trying the "HDA Intel" device, but it still didn't work. In addition, since the codec is seen as "IDT", I also tried the device called "IDT 92HD73C1X5 (OSS Mixer", but that didn't work either. Of course I need to mention there is options under both devices, and I'm not sure which option to select. 
Under the HDA Intel (ALSA Mixer), there is the following options:
> 
Master
Headphone
PCM
Front
Front Mic Mixer
Surround
Center
LFE
Line In Mixer
CD Mixer
Mic Mixer
Capture
Capture 1
DAC Mixer
I'm assuming the one I'm supposed to select is 'Master', so that is the one I tried it with, and it didn't work.
Then, under the IDT blah blah device, there is the following options:
> 
Volume
PCM-2
In-gain
Digital-1
The one that I tried was the 'Volume' option, and that doesn't work either. 
Any other suggestions? :P
BTW, I have not looked over those last couple of links yet in great detail, and will proceed to do that now.

Thanks again.

---

### Post by Jammanuser on 2009-04-21
It WORKS! \\:D/ I got it to work. 
After reading one of the last links you pointed me to ( [http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html](http://www.avalpa.com/assets/andrea/studio15/debian_on_dell_studio15.html) ), I read this quote:

> # **the only HP jack working (there are two in this Dell Studio) is the middle one!**
# the other HP jack near the front of the laptop (HP2) doesn't work
# if i plug a HP in the HP2 jack the IS quit the audio playing (if i unplug, the IS restart)
# Analog Loopback 1 toggle doesn't do nothing at all (neither for IS, nor for HP and HP2)
So right away I put the earphones in my middle jack, and it worked right away! :mrgreen: Of course there *was* a slight problem with the master volume not turning down the headphone volume...so when I went and played a song, it made me jump right out of the water because it was turned to max and I couldn't turn it down! :lolflag: But that was only because I had the "Headphone" option under the "HDA Intel (Alsa Mixer" device in System>Preferences>Sound (under the "Default Device Mixers" line) selected, so I would have needed to adjust the headphone volume to turn it down, but once I turned it to "System", right away, it would respond when I use the volume controls above the keyboard...
It will be cool if I can get both jacks to work though. Let me though if you have any thoughts on that. At least one of them works now.

Much appreciation and thanks for all your help.

Regards,

Jam man

:guitar:

---

### Post by Jammanuser on 2009-04-21
For all those who might have a similar issue, here is a summary of what needs to be done to get the middle headphone jack working on the Dell Studio 1535:

**Run the following commands in the Terminal:**
```
sudo killall pulseaudio
sudo alsa force-reload
```
**Open up System>Preferences>Sound:**
Under the Devices tab, change the selections under **Sound Events**, **Music and Movies**, **Audio Conferencing** to "ALSA-Advanced Linux Sound Architecture". Under **Default Mixer Tracks**, change the device to "HDA Intel (Alsa Mixer)". There should be a choice of options below that, such as "Master", "Headphone", etc. Make sure it is set to "Master".

**Double-click on the sound icon on the Gnome taskbar:**
The Volume Control for the HDA Intel (Alsa Mixer) will open. Click on the **Preferences** button. The Volume Control Preferences window will open. Tick the "Surround" option if not already selected. Do the same to the "Headphone as Line Out" option. Click **Close**. You should now see a new channel open up in the Volume Control, under the **Playback** tab, called "Surround". Verify that that channel is turned up to max, as well as the "Headphone" and "PCM" channels. 
**Important:** Turn down the "Front channel" all the way, so that the sound only comes out of the earphones, and not the speakers as well.
Now, click on the **Switches** tab in the Volume Control window, and tick the option called "Headphone as Line Out" if not already selected.

**Run the following command in the Terminal:**
```
gksudo gedit /etc/modprobe.d/alsa-base
```
This will open up the "alsa-base" file where you can adjust the configuration options for the alsa mixer. But you will first need to type your user account password before the file will open, as it is for modifying parts of your system. 
In the part of the file that has the following text,
> options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
add the following line,
> options snd-hda-intel model=dell-m6
after
> options snd-atiixp-modem index=-2
Press the **Save** button, and exit the file. You may have to restart or log of, and log back on, before the changes work.
Your middle headphone jack should now work, and the volume can be adjusted by using the master volume for the system.

-Jam man

:guitar:

---

### Post by vernonrj on 2009-04-22
Awesome. I am very pleased that I finally dug something up that helped you.

---

### Post by Jammanuser on 2009-04-22
Thanks man. :)
Very much appreciation.
I hope it'll help future users with the same problem.

---

### Post by vernonrj on 2009-04-22
I'll probably keep this bookmarked in case I run into something like this in the future. If anyone else has problems and you're reading this, I'll probably also keep a subscription to this for awhile, so post if you need help.

---

