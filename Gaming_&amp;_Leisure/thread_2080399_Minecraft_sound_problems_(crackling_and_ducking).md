---
title: "Minecraft sound problems (crackling and ducking)"
date: 2012-11-04
forum: Gaming &amp; Leisure
---

### Post by munchluxe63 on 2012-11-04
After simultatiously updating java (to 1.7.0_09)  and minecraft (to 1.4.2), I've been experiencing some extremely annoying and distracting sound issues.

About half the sounds in the game crackle or rapidly duck between left and right sound channels.

> daniel@Daniel-Ubuntu-L502X ~ % java -version
java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.10.1)
OpenJDK 64-Bit Server VM (build 23.2-b09, mixed mode)

---

### Post by 28c64 on 2012-11-04
Can you try launching Minecraft in a terminal with this command, then tell me if it fixes the sound issues?

```

padsp java -jar /path/to/minecraft.jar

```

---

### Post by munchluxe63 on 2012-11-04
> **28c64 said:**
> Can you try launching Minecraft in a terminal with this command, then tell me if it fixes the sound issues?

```

padsp java -jar /path/to/minecraft.jar

```

It doesn't make any difference.

---

### Post by 28c64 on 2012-11-04
Backup your .minecraft folder and try this?

```

cd ~/Downloads; wget -O lwjgl-2.8.3.zip http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download?use_mirror=iweb&r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&use_mirror=softlayer%3B; unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

```

---

### Post by munchluxe63 on 2012-11-04
> **28c64 said:**
> Backup your .minecraft folder and try this?

```

cd ~/Downloads; wget -O lwjgl-2.8.3.zip http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download?use_mirror=iweb&r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&use_mirror=softlayer%3B; unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

```

Still no difference.

Anyway, if it's worth mentioning, I'm using a 64-bit computer.

Edit: I have a crappy little USB sound card... I'll test it out and see if that changes anything.

---

### Post by 28c64 on 2012-11-04
Just something to mention. I see (now) you're using OpenJDK 7. I had multitudes of issues with the sounds. About half of the sound file just wouldn't work when I was playing Minecraft. I downloaded OpenJDK 6 and it fixed my problems.

---

### Post by munchluxe63 on 2012-11-04
> **28c64 said:**
> Just something to mention. I see (now) you're using OpenJDK 7. I had multitudes of issues with the sounds. About half of the sound file just wouldn't work when I was playing Minecraft. I downloaded OpenJDK 6 and it fixed my problems.

I just tried out OpenJDK 6 and it may have fixed the weird panning issues, but the sound is still very crackly.

Also, no luck with the USB sound card.

---

### Post by ambroseangle on 2012-11-06
I experienced same crackly sound problem in the game when I installed open JDK6 in my system. Could anyone help me which openJDK or Oracle should be installed. How can I access the game with out any sound problem?

---

