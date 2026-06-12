---
title: "Some Sound Problems......"
date: 2008-12-22
forum: General Help
---

### Post by Youbuntoo44 on 2008-12-22
Hello all. I really want to customize the sound Ubuntu makes when I log on successfully. I mixed my own little version of Daft Punk's song 'Technologic' that lasts about 10 seconds that I want to play, it is a .wav made with Audacity. The computer can play it just fine but whenever I attempt loading it onto System-> Administration -> Login Window, It shows that It knows where the file is, but when I click the play preview button it doesn't play and the same for when I am actually logging in. All the other .wav files it comes with play just fine. I put my file into File System->usr->Share->Sounds. What can I do for this to work? Thanks.

---

### Post by Wartender on 2008-12-22
go to system->preferences->sounds and under the sounds tab change the login sound.

---

### Post by Youbuntoo44 on 2008-12-22
??
[IMG]http://i43.tinypic.com/2qm2s86.png[/IMG]

---

### Post by Wartender on 2008-12-22
weird. i don't know :\

---

### Post by Youbuntoo44 on 2008-12-23
Thanks for helping anyway. :)

---

### Post by tbzep on 2008-12-23
I have a problem that is probably related.  I wanted to change my login sounds also, so I found a .wav I liked and changed it under system/administration/loginwindow/accessability, after putting the file in the usr/share/sounds folder.  It would not play them at boot.  

After searching, I found an article that said they needed to be changed from 16bit to 8bit.  I used Audacity to do this and I was able to get the sounds at boot.  Unfortunately, it killed **all** sound on everything else.  I realized it when I surfed to Youtube and got video with no sound.  Trying to find out why I couldn't get Youtube sound, I soon found out that all audio and video programs except Audacity locked up when trying to play any type of sound file, including the boot .wav. Audacity would still play any sound files without crashing for some reason.

I switched back to the ubuntu default sound and rebooted and got all my sound back.  I've been fooling with this for a while now.  At first, I thought it was a flash problem so I removed it and installed the new 10 alpha. I then decided I wanted to go with Intrepid anyway so I reformatted and did a fresh install of everything.  I got sound immediately and thought that would solve my problem.  The second I put the converted 8bit files back into the login, my problems returned.

**To make a long story short, you probably need a very specific .wav format for this to work without screwing up the rest of your system. I'm still trying to figure out exactly what will work.**

I was running 64-bit Hardy, Flash 9 and then 10 alpha, now 64-bit Intrepid with 10 alpha. Same results with all combinations.

---

### Post by tbzep on 2008-12-25
Finally got everything working.  In order not to kill off all sound on the computer, my custom login sounds had to be saved as:

Uncompressed 16-bit PCM audio

44100 Hz

The sound samples that were killing my computer sound originally had 16000 Hz sample rates.  When I changed to 8-bit, they would play at login but killed all other sound on the computer from that point forward.  Going back to 16-bit and converting to 44100 Hz sample rate did the trick.

I used Audacity to convert and ```
gksudo nautilus
``` in order to be able to save files in the usr/share/sounds folder.

---

