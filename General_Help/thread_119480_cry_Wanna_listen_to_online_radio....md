---
title: "*cry* Wanna listen to online radio..."
date: 2006-01-19
forum: General Help
---

### Post by Minyaliel on 2006-01-19
... but I can't figure out how because when I click on a link, there's this window coming up asking me whether I want to play it or download it and whatever I do, nothing really happens. I'm running amaroK, if that's any help. All other media works, but not the live streams... *sob*

---

### Post by obibok on 2006-01-19
Right-click on this radio link, copy its location and paste it here. Someone should be able to help you figure out what to do from there.

---

### Post by skaboss on 2006-01-19
In order to listen to online radio, you have to click "open with" within your browser, and then select your player (amarok, for example), or the path to it.
If it doesn't work, it's probably a problem with your firewall.
Could you try to disable your firewall and then open a stream ?

---

### Post by stream303 on 2006-01-20
[QUOTE=Minyaliel]... but I can't figure out how because when I click on a link, there's this window coming up asking me whether I want to play it or download it and whatever I do, nothing really happens. I'm running amaroK, if that's any help. All other media works, but not the live streams... *sob*[/QUOTE]

No problem!   Here's what works well for me - I configure it old-school although I'm a fan of Rhythmbox - the following is pretty generic however ;) 

If you intend to listen to mp3 or AAC streams, you'll need to enable the universe and/or multiverse repositories to get the proper codecs.  Let's use gstreamer codecs as an example so you can listen to radio with Rhythmbox.

Using synaptic or apt-get, for **mp3** download **gstreamer0.8-mad**
For **aac** decoding, download **gstreamer0.8-faad**

1) Click the streaming link with the format of your choice in your browser.

2) If a dialog box appears asking you if you want to choose an application or save the file to disk, I save it to disk!  (usually some sort of playlist, .pls file what-have-you)

3) use an editor (gedit, nano, whatever) to look inside this file.  You'll find the proper http address of the "channel"  You might find several lines of channel url's there which should be self-explanatory as to which one you really want.

4) Now open up Rhythmbox, right-click on the radio icon, and add a new station using the address we found in step 3 by placing the url in the location box.

5) Click the play button and enjoy!

This was the technique that allowed me to properly use command-line players like mpg321 etc.  **I just wish that more stations would use Ogg-Vorbis codecs.**

---

### Post by Jolva on 2006-01-20
I hate to bump in, but I have a question along the same vein. I really dig this station located here: [www.wdox.com](www.wdox.com). However, they use the .asx format. Which I *think* is a proprietary Windows Media Player format. I've tried amarok and XMMS - neither seem to work. Thanks for the help if anyone knows! :p

---

### Post by shakin on 2006-01-20
[QUOTE=Jolva]I hate to bump in, but I have a question along the same vein. I really dig this station located here: [www.wdox.com](www.wdox.com). However, they use the .asx format. Which I *think* is a proprietary Windows Media Player format. I've tried amarok and XMMS - neither seem to work. Thanks for the help if anyone knows! :p[/QUOTE]

I just played that stream using Xfmedia. I don't really play any audio on my work computer so I didn't have much else installed. To make it play I downloaded the asx file and chose to open it with xfmedia in the right-click menu. It took a minute to buffer, then played perfectly.

---

### Post by Jolva on 2006-01-20
Thanks Shakin for the quick reply! I'll give that a go when I get home. :p

---

### Post by Minyaliel on 2006-01-20
It works! Thank you!! *wee!*

---

### Post by semaphore on 2006-05-26
[QUOTE=shakin]I just played that stream using Xfmedia. I don't really play any audio on my work computer so I didn't have much else installed. To make it play I downloaded the asx file and chose to open it with xfmedia in the right-click menu. It took a minute to buffer, then played perfectly.[/QUOTE]

Thanks for the tip, but how can I install Xfmedia for Breezy?

---

### Post by ingo on 2006-05-26
type

sudo apt-get install xfmedia 


if apt-get cannot find it enable the "universe" repository in synaptic file manager

---

