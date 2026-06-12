---
title: "[SOLVED] no sound from firefox"
date: 2008-06-06
forum: Desktop Environments
---

### Post by dzisler on 2008-06-06
What do I have to install to get sound from firefox. I have sound for everything else(Audio players) but when I visit you tube there is no sound. What am I missing?

---

### Post by Bubba64 on 2008-06-06
> **dzisler said:**
> What do I have to install to get sound from firefox. I have sound for everything else(Audio players) but when I visit you tube there is no sound. What am I missing?

Are you getting any sound at all, and have you included medibuntu in the 3rd party, and have you installed ubuntu restricted extras in add remove along with the gstreamer and ffmpeg extras there and vlc.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dzisler on 2008-06-07
I have sound in all the media players but not in the web browser, added gstreamer and ffmpeg what is vlc?

---

### Post by trevelyan on 2008-06-07
are you using the media players when you run firefox? if so thats why.
ubuntu doesnt play sound from more than one application at a time.. try closing all the media players and try firefox again..

i read somewhere that switching everything in system > Preferences > Sound  to pulse audio fixes that and allows you to hear sound from multiple applications at once.. but for me that didnt work. :(

---

### Post by NilsE on 2008-06-07
Also, if it is flash that you are not getting sound in then install libflashsupport

---

### Post by trevelyan on 2008-06-07
hey.. scratch what i said before.. changing everything to pulseaudio did work... i guess the changes took effects after i rebooted. :D 
anyways.. give it a try. and reboot to make sure.

---

### Post by Bubba64 on 2008-06-07
> **dzisler said:**
> I have sound in all the media players but not in the web browser, added gstreamer and ffmpeg what is vlc?

Vlc is another media player in add remove that has a library for decoding types of media. If you you have all of my suggested installed. A type of media should open automatically when you click on play from your browser or open as part of a auto detect in a website. The libflash should have been installed as part of the suggested package , but you can look in synaptic to see if it has. Medibuntu I think has some of the stuff that the add remove asks for when installing the suggested packages. In FF preferences you can change the type of player for type of media, although I have never had to do this except on downloaded stuff, except for personal preferences.

---

### Post by jpietari on 2008-06-07
If you try to play a youtube video while playing a music in Banshee, you'll have no sound.  As described, installing libflashsupport will correct this problem.

The bug report already has been filed

---

### Post by Bubba64 on 2008-06-07
The one additional package I always install is alsa/oss in synaptic so either will be read I assume. I know I see Libflash problems posted but personally I have never had a problem in accessing just about any media but I have some pretty old hardware that doesn't need anything but generic drivers.

---

### Post by dzisler on 2008-06-07
Added libflashsupport and now have sound sweeeeeeeeeeeet! Thanks to all. I am going to work thru this and migrate away from windows. With support like this it is great

---

