---
title: "no sound in java when changing to Sun Java"
date: 2009-01-25
forum: General Help
---

### Post by martindp on 2009-01-25
Hi!

Recently I had to change my Java RE to Sun's, because an application would crash occasionally using the default one. Now the application works fine, except that I don't have any sound anymore (within that application - otherwise sound works ok).

I use ALSA in Intrepid and Sun JRE 6. I had a look in Synaptic, but couldn't find any obvious packages I might be missing.

Any help much appreciated!

---

### Post by fugyfudy on 2009-02-02
I'm having this same problem.  I'm sorry that I don't have a solution but it's really bugging me because my online classes rely on me having Java fully functioning, and I'm sick of booting into Vista all the time.  Just hoping for some help.

---

### Post by Dartr on 2009-03-09
Same issue here.  I can record sound into an Elluminate session (online class) but can't hear playback.

Intrepid 64
Sun Java Web Start 5

---

### Post by Therion on 2009-03-09
Kind of a longshot, but give this a go...

Open Synaptic.
Search on "Gnash".
Mark any found "Gnash" packages for removal.
Log out, Log in, restart Firefox.

---

### Post by Dartr on 2009-03-09
no Gnash packages installed.  :(

---

### Post by Gerard Aksomitis on 2009-09-30
If you are trying to use Elluminate in Ubuntu I have manged to get it to work by going to the Elluminate web page and going through their configure sound section.

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

