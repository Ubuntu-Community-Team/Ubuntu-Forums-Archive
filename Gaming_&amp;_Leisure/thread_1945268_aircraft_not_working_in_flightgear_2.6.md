---
title: "aircraft not working in flightgear 2.6"
date: 2012-03-22
forum: Gaming &amp; Leisure
---

### Post by gandalf3 on 2012-03-22
I'm new to Linux, and installed Ubuntu 11.10 about a month ago and decided to try downlading some extra aircraft for Flightgear 2.6
most worked, but some did not..

I've had problems with the following aircraft: (in no particular order)

X15   (is not visible in any view)

Hawker SeaHawk (on clicking "run" the log window prints this..)

```
Error reading aircraft: Cannot open file
 at ../../Input/Keyboard/carrier-bindings.xml
Config option parsing failed ...
```WrightFlyer1903   (when "initilzing subsystems" log prints:

```
Fatal error: Unrecognized flight model 'larcsim', cannot init flight dynamics model.
AL Error (avionics): 
```Vostok-1 (prints the following, then crashes)

```
FGPropertyManager::GetNode() No node found for /position/sea-level-radius-ft
no image file, maybe the reader did not set the filename attribute, using white for type '2d' on '', in /technique[9]/pass[0]/texture-unit[0]
creating 3D noise texture... DONE
```Stiletto (won't extract, command line output:

```
Archive:  /home/user/Downloads/Stiletto_20111001.zip
[/home/user/Downloads/Stiletto_20111001.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/user/Downloads/Stiletto_20111001.zip or
          /home/user/Downloads/Stiletto_20111001.zip.zip, and cannot find /home/user/Downloads/Stiletto_20111001.zip.ZIP, period.
```a4 (same as wrightflyer, exept it crashes immediately)

BlackBurn Buccaneer (also not visible, here's a screen shot..)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214791&stc=1&d=1332464904[/IMG]
prints: ```
Nasal runtime error: undefined symbol: setlistener
  at /usr/share/games/flightgear/Nasal/aar_jsbsim.nas, line 48
Animated jetways ... initialized
loading scenario 'nimitz_demo'
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
creating 3D noise texture... DONE
weather util initialized ...
Initializing Buccaneer utilities ...
pilot-g
pilot headshake
observer headshake
smoke
index0
variant index: Side No 322 1
index0
variant index: Side No 323 2
variant index: Side No 324 3
variant index: Side No 325 4
running Buccaneer Observer utilities
Copilot dual control ... initialized
```
so far, that's everything that's not working..](*,)

---

### Post by catlover2 on 2012-03-24
[Here](http://www.flightgear.org/mail.html) is FlightGear's support page; there will be many more people who are knowledgeable about FG issues over there than on these forums

---

