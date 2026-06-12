---
title: "UT2004 Text to Speech"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by tjb891 on 2006-07-27
Ok I have installed Unreal Tournament 2004 and it works great (much much faster than on XP) but I am having trouble enabling Text to Seech(TTS). I know that it is possible and it has to do with festival but thats about it. I have  the full game, not the demo. Can anyone help me?

---

### Post by lavinog on 2008-06-08
I would like to know if anyone got text to speech (TTS) to work in ut2004?
UT2004 will output all messages to a file set in the ut2004.ini file.
I have verified that this works by reading the file while the game is being played.
I have also come up with a way to use espeak to read the file every 2 secs using 'watch'
The problem is that espeak will not output sound while the game is running.
This is really frustrating...I have tried a couple of speech engines, but I guess it is a limitation... i get an error: ```
Linux: can't open /dev/dsp

```
I guess I could share the file and have another computer read it...wow that would be weird.

---

### Post by lavinog on 2008-06-08
Ha I just solved it.
searching the forums for can't open /dev/dsp gave me my answer:
Specifically this post: [http://http://ubuntuforums.org/showpost.php?p=4918148&postcount=20]("http://ubuntuforums.org/showpost.php?p=4918148&postcount=20")

apparently festival uses oss instead of alsa...by telling it to use alsa I am able to hear the text to speech engine and the game at the same time.

Right now I am just using the following:
```
watch -n 1 'festival --tts <TextSpeak.txt && cat /dev/null >TextSpeak.txt'


```
and my ut2004.ini file has this:
```
TextToSpeechFile=/home/greg/TextSpeak.txt
```
under the [SDLDrv.SDLClient] section

---

