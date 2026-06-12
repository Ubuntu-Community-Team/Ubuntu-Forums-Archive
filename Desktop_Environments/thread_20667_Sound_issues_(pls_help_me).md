---
title: "Sound issues (pls help me)"
date: 2005-03-17
forum: Desktop Environments
---

### Post by inphlict on 2005-03-17
Hello I'm very new to linux, 

Anyway I'm having issues with mplayer and sound. When i try to run a file I get "audio_setup: Can't open audio device /dev/dsp: Device or resource busy"

I've found two ways to fix this but they have problems :(

First one is "killall esd" & second one is by disabling sound server startup in Sound Preferences. When I do this I get sound, but I have problems with Rhythmbox when i try to play anything I get "Could not open resource for writing." & then I get "Could not pause playback" in Rhythmbox.

Thanks for your help guys :)

EDIT: Forgot to add I'm running hoary.

---

### Post by bored2k on 2005-03-17
[QUOTE=inphlict]Hello I'm very new to linux, 

Anyway I'm having issues with mplayer and sound. When i try to run a file I get "audio_setup: Can't open audio device /dev/dsp: Device or resource busy"

I've found two ways to fix this but they have problems :(

First one is "killall esd" & second one is by disabling sound server startup in Sound Preferences. When I do this I get sound, but I have problems with Rhythmbox when i try to play anything I get "Could not open resource for writing." & then I get "Could not pause playback" in Rhythmbox.

Thanks for your help guys :)

EDIT: Forgot to add I'm running hoary.[/QUOTE]
 sudo apt-get install vlc vlc-esd vlc-plugin-esd then open vlc ^_^
or just install xine-ui totem-xine

---

### Post by inphlict on 2005-03-17
[QUOTE=bored2k]sudo apt-get install vlc vlc-esd vlc-plugin-esd then open vlc ^_^
or just install xine-ui totem-xine[/QUOTE]
 I thought I was fixing it but I installed another player :( I acctually want to solve mplayer problem.

Now how do I remove vlc? 

Thnx

---

### Post by bored2k on 2005-03-17
[QUOTE=inphlict]I thought I was fixing it but I installed another player :( I acctually want to solve mplayer problem.

Now how do I remove vlc? 

Thnx[/QUOTE]
 sudo apt-get remove vlc

---

### Post by inphlict on 2005-03-17
Thanks, I think i fixed it after installing ALSA or whatever. I still get problems if I run 2 apps that use sounds at the same time but seprate it works. Anyway I can run video and mp3 play at the same time :)

---

### Post by bored2k on 2005-03-17
[QUOTE=inphlict]Thanks, I think i fixed it after installing ALSA or whatever. I still get problems if I run 2 apps that use sounds at the same time but seprate it works. Anyway I can run video and mp3 play at the same time :)[/QUOTE]
 that is  way you are advised to use eSound. this way you will get multiple sounds.
but, whatever suits your needs .

---

