---
title: "Dell Optiplex 745 Sound On Speakers And Headphones"
date: 2013-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gilad_Pellaeon on 2013-08-14
I tried to post in this thread on a better solution I found at least with Lubuntu 13.04 on how to fix sound coming out of both headphones and internal speakers in the tower using the integrated sound built into the tower at the same time that doesn't involve using gnome-alsamixer which for me had crashed in LXterminal with a segfault. I uninstalled gnome-alsamixer afterwards. Would it be possible to add my solution to the closed thread?

Closed Thread:
[URL="http://ubuntuforums.org/showthread.php?t=1474729"]http://ubuntuforums.org/showthread.php?t=1474729
[/URL]
My Solution:

1) Right Click on the volume icon in Lubuntu 13.04 and click "Volume Control" settings. 

2) This brings up a mixer with a GUI of sorts

[IMG]http://u.cubeupload.com/Pellaeon2/alsamixerdelloptiple.png[/IMG]

3) Use left or right arrow keys to navigate and up and down to turn volume up and down. In this case I kept using right arrow until the word Mono is highlighted in red and in < > brackets. Then press down arrow key until it is at 00. You can easily test this as an example by having Audacious playing an mp3, ogg, or whatever kind of sound file on your headphones, then press up arrow key on Mono and listen to the sound get louder on the internal tower speakers. Crank it back down to 00 and it's muted again so you can listen to your audio in headphones in peace without having the internal speakers blasting away too. :)

---

