---
title: "Runescape - No sound when game is running."
date: 2010-04-02
forum: Gaming &amp; Leisure
---

### Post by Screatch on 2010-04-02
When i am playing a java based game Runescape, i can hear sound and music in Runescape, but can't hear any outside of runescape.. i can't listen to music or watch youtube.. nothing...

What could be the problem and is there a fix?

---

### Post by doorknob60 on 2010-04-03
Make sure nothing that could be using the sound card is open, including Youtube videos, music players, etc before you start Runescape. Yeah, Java sucks balls on Linux, fix it Sun!!

---

### Post by Screatch on 2010-04-03
Nothing that uses sound card is not open..
You see what is happening.. if i happen to open musical player or youtube video before running runescape, there will be no sound on runescape but atleast i will be able to play music and watch videos..

If i start runescape first and then audio player, runescape sound countinues to play but any other sound including notifications doesn't work..

There is no fix at all?

---

### Post by Piro24 on 2010-04-03
I used to have this problem. It depends on what sound-server you use (ALSA/OSS/PulseAudio/etc), along with the programming of each particular program.

For example, I can play music with Rhythmbox and watch videos with FireFox at the same time. However, if I try to do some video editing with Kdenlive, I have to make sure nothing is using the sound service other than Kdenlive.

I haven't had this problem in awhile, but try changing your sound-server, I personally use Pulseaudio.

---

### Post by doorknob60 on 2010-04-03
> **Screatch said:**
> Nothing that uses sound card is not open..
You see what is happening.. if i happen to open musical player or youtube video before running runescape, there will be no sound on runescape but atleast i will be able to play music and watch videos..

If i start runescape first and then audio player, runescape sound countinues to play but any other sound including notifications doesn't work..

There is no fix at all?

Well, there's some fixes that work sometimes, and sometimes you think you finally found something that works, but it ends up making RS crash after an hour or so. I don't use Pulseaudio (Ubuntu does by default), so I'm not sure how this would work, but I know if use use aoss you can get RS and other sounds to play at the same time, but it makes RS randomly crash (don't ask me why), so I don't do that. What I do is if I want to hear RS sound, I open that first, if I want to hear other sound, I open that first. Or set my laptop next to my desktop and use them both :P This bug has been in Sun's bug tracker since 2005, and it still hasn't been fixed. Also you could try Wine (installing the Windows version of Firefox and Java in Wine). Sometimes that works great, but for me it doesn't (I screwed up Wine's Java and it won't let me reinstall). Worth a try though.

---

### Post by Mr_Bumpy on 2010-06-21
I had the problem under Ubuntu Lucid where the sound output from Java apps would conflict with the sound output from other programs.  In other words, I couldn't play an MP3 and get sound output from the Runescape login screen simultaneously.  I did it by following these steps:

1. First, you will need to rename the java executable, and put another command in its place.  Enter the following commands using the terminal:
```
cd /usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java
```
2. Now, copy and paste the following into the nano editor window, then press CTRL-X to exit and Y to save changes:
```
#!/bin/bash
padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
```
3. Restart Firefox if it is open, then test the sound.  An easy way is to visit this page: [http://javaboutique.internet.com/Guitar/]("http://javaboutique.internet.com/Guitar/").  Play around with the sounds, and then try to play an MP3 or something on your computer.  While the MP3 is playing, see if you can still hear the guitar sounds when you click on the buttons.

If it works, you may want to lock all of the sun-java6* packages at their current version in Synaptic, otherwise a future Java update may break this hack, and you'll have to do it all over again.

---

### Post by doorknob60 on 2010-06-28
> **Mr_Bumpy said:**
> I had the problem under Ubuntu Lucid where the sound output from Java apps would conflict with the sound output from other programs.  In other words, I couldn't play an MP3 and get sound output from the Runescape login screen simultaneously.  I did it by following these steps:

1. First, you will need to rename the java executable, and put another command in its place.  Enter the following commands using the terminal:
```
cd /usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java
```
2. Now, copy and paste the following into the nano editor window, then press CTRL-X to exit and Y to save changes:
```
#!/bin/bash
padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
```
3. Restart Firefox if it is open, then test the sound.  An easy way is to visit this page: [http://javaboutique.internet.com/Guitar/]("http://javaboutique.internet.com/Guitar/").  Play around with the sounds, and then try to play an MP3 or something on your computer.  While the MP3 is playing, see if you can still hear the guitar sounds when you click on the buttons.

If it works, you may want to lock all of the sun-java6* packages at their current version in Synaptic, otherwise a future Java update may break this hack, and you'll have to do it all over again.

I'll confirm that this seems to work so far on Arch (I just switched to Pulseaudio so I can try it out). So far so good :) You need to change the path in Arch because Java's in a different spot, but yeah it works.

---

### Post by Theredbaron1834 on 2011-06-04
I know this is an old topic, but the top topic when searching didn't help, so I thought respond and say that Sun still hasn't fixed it, and this little hack still does., with Ubuntu 11.04.

---

### Post by gylti on 2011-07-03
I tried this but now runescape doesnt even load i get a grey screen and have to restart browser

---

### Post by doorknob60 on 2011-07-07
More recently for me, OpenJDK seems to work just fine with Pulseaudio without using any weird hacks. Sun Java still doesn't work, but OpenJDK does. If it doesn't work right in a browser, I've noticed that sometimes it works better with the official client, here's a guide on how to set that up, that's what I use and it works great: [http://forums.zybez.net/topic/1436346-guide-linux-native-official-rs-java-client/](http://forums.zybez.net/topic/1436346-guide-linux-native-official-rs-java-client/)

---

