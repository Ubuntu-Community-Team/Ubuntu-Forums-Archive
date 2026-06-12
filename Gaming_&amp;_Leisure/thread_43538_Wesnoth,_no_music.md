---
title: "Wesnoth, no music?"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by Prudentissimus on 2005-06-22
Hi,

Is there in-game Music for Wesnoth? I'm not hearing any...

Please help.

---

### Post by d3s on 2005-06-23
[QUOTE=Prudentissimus]Hi,

Is there in-game Music for Wesnoth? I'm not hearing any...

Please help.[/QUOTE]
 Yes there is music, if you installed it.
probably your sound device is used by other program, anyway try to open wesnoth in terminal and then you will see what the problem is.

---

### Post by Zeddicus on 2005-06-23
As the above poster somewhat mentioned -- make sure you've installed the music!  Installing Wesnoth doesn't pull in the music by default, which is held in another package (wesnoth-music).

---

### Post by afonic on 2005-06-23
In case you have the music installed and you don't hear it (I guess the other sounds as well then) type in the console:

killall esd

---

### Post by josephwalter on 2005-06-23
"killall esd" got the sound working on my computer. Thank you, afonic.

How do I start the esd process again when I'm done playing?

Is there a way to configure esd so that I don't have to kill the process to get sound in wesnoth?

---

### Post by afonic on 2005-06-23
[QUOTE=josephwalter]"killall esd" got the sound working on my computer. Thank you, afonic.

How do I start the esd process again when I'm done playing?

Is there a way to configure esd so that I don't have to kill the process to get sound in wesnoth?[/QUOTE]
 You're welcome.

If you follow this thread you can make sound working without killing esd:
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

However this created some problems for me (low quality system sounds) and I had to disable it, but in my laptop it worked ok, so I guess it depends on the soundcard, give it a try.

---

