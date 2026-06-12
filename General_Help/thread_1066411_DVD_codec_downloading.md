---
title: "DVD codec downloading???"
date: 2009-02-10
forum: General Help
---

### Post by nboy56 on 2009-02-10
I recently tried to play a dvd in my ubuntu 8.10 computer the totem player said i needed to get a codec so i looked online and it said i had to enter some code into terminal or synaptic really my question is really about downloading using these "codes" so could someone give me a in depth step by step walkthrough on how to download with a code 

Basically i need someone to give me a way to play encrypted dvds on my computer (be it codecs for totem or a totally new media player) and I also need full step by step instructions on how to download stuff with ubuntu 8.10

---

### Post by taurus on 2009-02-10
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mike555 on 2009-02-10
You should check out the  site;  [http://www.medibuntu.org/](http://www.medibuntu.org/)   for DVD's   .... if you want to install programs you should use the "add/remove" or your package manager.......

---

### Post by mb_webguy on 2009-02-10
"Codec" stands for either "coder/decoder" or "compressor/decompressor", depending on who you ask.

In a nutshell, uncompressed video is friggin' huge.  To make it a more reasonable size, it has to be compressed (or encoded).  It's sort of like a court reporter's shorthand.  There are many different types of encoding.  If you don't know how to read it, it's meaningless.  Without the right sooper-sekrit decoder ring (i.e. codec), encoded video is just gibberish to your computer.  It's completely indecipherable because the computer doesn't have the cipher.  The codec tells the computer how to extract the encoded video into playable video.

Some DVDs have a certain form of content protection called CSS ("Content Scrambling System"), which is sort of an extra encoding over and above the normal encoding.  The movie industry developed this as a (futile) attempt to prevent people from making copies of DVDs (even when they may have a perfectly legal right to do so).  The movie industry naturally didn't want to release the method of decoding CSS to the open-source community, because then anyone could do it.  They preferred to license the CSS key to commercial software, keeping it a secret while making a few extra bucks.  Fortunately, the open-source community is nothing if not resourceful, and not very happy when people try to curb their legal rights, and figured out a way around CSS encryption in short order.  

However, because this is a gray area in some parts of the world, Ubuntu can't include this in their distribution by default, so they put it in a separate repository that must be manually added by the user to transfer any possible legal or ethical burdens that may arise due to differing legal codes around the world to the user.  They place codecs for proprietary audio and video formats in this separate repository for the same reason.

What this means for you is that all you have to do in order to play any darn thing you want on your computer is to add the Medibuntu repository and install a few packages.

---

### Post by nboy56 on 2009-02-11
Ok I have a suitable codec downloaded but totem plays dvds at a super choppy rate and doesnt have any sound and does anyone know how to get vlc player on ubuntu 8.10 or another player that can play encrypted dvds or do I need another download for totem Once again plz give step by step instructions

---

### Post by oldos2er on 2009-02-11
Not sure which codec you mean, is it libdvdcss2? You can install via the link Taurus gave you.

 You install vlc just like any other program, in a terminal enter
```
sudo apt-get install vlc
```

 Or open Synaptic Package Manager and search for vlc.

---

### Post by nboy56 on 2009-02-11
vlc doesnt show up in synaptic

---

### Post by mb_webguy on 2009-02-11
Make sure you have the multiverse repository checked in software sources.

OR, you can download the most recent release from [here]("http://archive.getdeb.net/dump/intrepid/vlc/").  You don't need all of the plugin packages (except probably Pulse), but you do need all of the others.  Make sure you get the same version for each of the packages.  Once you've downloaded them all, switch to the terminal, cd to the directory where you downloaded the packages, and type "sudo dpkg -i *.deb".

---

