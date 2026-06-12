---
title: "Sound is mostly working...but PLAY and APLAY dont work!"
date: 2005-05-01
forum: Desktop Environments
---

### Post by haldrik on 2005-05-01
Hi Everyone:
I finally got my sound working mostly...
KDE sounds work fine, xine, xmms, amarok and other media players work fine using arts. (I've tried OSS and esd as well, but have had most sucess using arts)
My two outstanding issues are that
1)  play and aplay don't work, they just freeze with the message:
 will@localhost:~$ play /usr/share/sounds/pop.wav
playing /usr/share/sounds/pop.wav

(but nothing happends and I have to cntrl-c my way out of it. Same with aplay, only with that I don't even get the "playing.." message.)

2) Also, sounds WITHIN firefox/mozilla and thunderbird don't work either (maybe they use "play" to do their sounds, who knows...). Like when I set a sound in thunderbird and try to "test" it, there's no sound at all.
I remember that when I tried using esound (which had countless other problems) the sounds in thunderbird did actually work. Links to .wav files in firefox likewise produce nothing.

Anyone have similar problems and (maybe) a solution or two?

THanks and have a great day!

---

### Post by Professor X on 2005-05-01
Have you tried using artsdsp to play a sound?  It works the same way as play/aplay.  The issue might be that play/aplay is not configured to use aRts (aRts won't release control of your sound card).

---

### Post by haldrik on 2005-05-03
Well, that was great (and quick!) advice!!!...got PLAY to work through artsdsp!!! Thanks!
Now, how can I get Mozilla/Firefox and Thunderbird to use arts as its default sound server? Maybe that would make the sounds work WITHIN those programs???

---

