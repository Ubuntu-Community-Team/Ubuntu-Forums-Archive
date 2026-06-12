---
title: "Sound issues in Minecraft"
date: 2010-10-09
forum: Gaming &amp; Leisure
---

### Post by Lyoko on 2010-10-09
Hello, I'm trying to play minecraft in 'lubuntu' a ubuntu distro, the  performance is a lot better than windows, but i cant get sounds in the  game. i tried pressing F3+s, Nothing.
i tried redownloading, deleting .minecraft folder, installing resources from windows machine, removing settings file.
nothing helped so far..
i hope you could help me, thanks.

---

### Post by donkyhotay on 2010-10-09
As with every minecraft related question...

What java are you using?

---

### Post by Lyoko on 2010-10-09
> **donkyhotay said:**
> As with every minecraft related question...

What java are you using?
I didn't try openJDK, i went directcly to Sun java 6 v21.."sun-java6-jre"

---

### Post by donkyhotay on 2010-10-09
Hmm... not certain in that case. That's the version of java I use to play minecraft on ubuntu. I sometimes run into odd graphical glitches and it occasionally goes out but always comes back when I at least restart the game (certain it's due to alpha status). I'm assuming you get sound from the computer in general of course, can you get sound from other java applications? If you don't have any other java apps have sound in them try running puzzle pirates real quick. You don't even need to make an account to test it, the initial login screen you see when the game firsts launches plays music. That will narrow down whether it's more of a java issue vs. a minecraft issue.

---

### Post by Lyoko on 2010-10-09
> **donkyhotay said:**
> Hmm... not certain in that case. That's the version of java I use to play minecraft on ubuntu. I sometimes run into odd graphical glitches and it occasionally goes out but always comes back when I at least restart the game (certain it's due to alpha status). I'm assuming you get sound from the computer in general of course, can you get sound from other java applications? If you don't have any other java apps have sound in them try running puzzle pirates real quick. You don't even need to make an account to test it, the initial login screen you see when the game firsts launches plays music. That will narrow down whether it's more of a java issue vs. a minecraft issue.

i have sound in java.. tried runescape...
btw. i installed OpenJDK instead of sun java, sound works, fps is terrible...

---

### Post by donkyhotay on 2010-10-09
Hmm... well it's definitely something between minecraft and java then. I'm not really certain anymore because I've never had consistent audio issues with minecraft and I've only ever used it with sun java 6 which is the same version you are using. I hate to admit it but you've got me stumped.

---

### Post by efikkan on 2010-10-10
The following sometimes helpes for me:
* Make sure to kill all running instances of java.
* Enter in terminal: sudo alsa reload
* Then enter: pulseaudio -k
* Restart the game.

Another tip is to not have any audio applications running when launching Minecraft.

---

### Post by bosshoff on 2010-11-25
Try using the 32-bit version of Java; fixed my prob.

[http://java.dzone.com/tips/32-bit-jdk-a-64-bit-ubuntu-sys]("http://java.dzone.com/tips/32-bit-jdk-a-64-bit-ubuntu-sys")

---

