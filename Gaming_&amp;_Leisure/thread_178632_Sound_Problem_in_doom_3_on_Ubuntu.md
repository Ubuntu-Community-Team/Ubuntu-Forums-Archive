---
title: "Sound Problem in doom 3 on Ubuntu"
date: 2006-05-18
forum: Gaming &amp; Leisure
---

### Post by muffinhead on 2006-05-18
I recently installed doom 3 in Ubuntu, via the Linux installer on my PC. But I am having a Problem with the sound.

When I play a game of Doom 3, the sound is garbled, and don't laugh but voices, and guns, sound like robots, and don't sound like they normally do. The sound cuts out also.

I have seen People  mention on this forum to open  a terminal and set your sound to OSS, But my whole problem is I Cannot set my sound to OSS, when I do, I have no sound, and when I test my sound via the Multimedia Selector System, with it set to OSS, I am Presented with an error Saying, 

"Failed to construct test pipeline for 'OSS - Open Sound System"

I've tried it both with my onboard Intel Realtek AC'97 Sound, and my Sound Blaster Live 24-bit, to no avail. With my Sound Blaster, I don't get any sound at all in games, and cannot choose either ALSA, or OSS.


If you can help me get my sound issue fixed, it'll be greatly appreciated, Thank You. 

It really bugs me to play with the sound messed up](*,) So if you can help me as soon as Posible that would be great, Thanks;)

---

### Post by etement on 2006-05-18
why not make Doom3 use OSS? 

open doom3.sh (in /home/username/doom3 if you installed to default dir)
Last line should look like this for OSS
```
exec ./doom.x86 "+set s_driver oss"  "+set NumberOfSpeakers 2"
``` 

I had the same problem before.

---

### Post by muffinhead on 2006-05-18
Thanks for Replying, but I tried opening the doom3.sh file, with gedit and nano, and the file is completely empty, no text or nothing.

I don't know if I can use OSS with my Sound Blaster Live 24-bit, everytime I try to use OSS, I have no sound completely, in Programs, or nothing. I don't know if OSS is compatable with my sound card.

If anyone else can help, It would be greatly appreciated, Thanks;)

---

### Post by dragonfyre13 on 2006-05-18
Is sound all skippy too? Mine is horrible like that, and I have searched everywhere for a solution.

---

### Post by etement on 2006-05-18
[QUOTE=muffinhead]Thanks for Replying, but I tried opening the doom3.sh file, with gedit and nano, and the file is completely empty, no text or nothing.

I don't know if I can use OSS with my Sound Blaster Live 24-bit, everytime I try to use OSS, I have no sound completely, in Programs, or nothing. I don't know if OSS is compatable with my sound card.

If anyone else can help, It would be greatly appreciated, Thanks;)[/QUOTE]

sorry. it's just called doom3. ](*,)  doesn't have .sh, but it's still intepreted as a shell script. This will fix your problem.

---

### Post by muffinhead on 2006-05-18
Thank you, I managed to get it fixed now, and it is working perfectly. Doom 3 runs better on Linux with my current setup, than it did on Windows XP:)

Thanks for the help, I really appreciate it;)

---

### Post by etement on 2006-05-18
[QUOTE=muffinhead]Thank you, I managed to get it fixed now, and it is working perfectly. Doom 3 runs better on Linux with my current setup, than it did on Windows XP:)

Thanks for the help, I really appreciate it;)[/QUOTE]

no problem. it works for quake4 as well.

---

