---
title: "Using mplayer, then lost keyboard and mouse"
date: 2005-04-15
forum: Desktop Environments
---

### Post by [censored] on 2005-04-15
Just had a nasty, serious system freeze using mplayer. I post the details below in the hope that someone can help me diagnose the problem, and maybe even help me to prevent it from happening in the future

Hi. Been using ubuntu 3 days now.

System: PIII Celeron 1.1Ghz, 256meg RAM, nvidia Gf4 128meg vid card.

standard 3d nvidia drivers, obtained via apt-get.

System seems to bottle necked in a major fashion.

Was watching an avi on mplayer using "-vo xv" option, while downloading stuff with apt-get, and chatting on irc with xchat. 

The keyboard stopped accepting input, and the mouse pointer froze. The movie kept running, so I continued to watch it until the screen saver appeared.

Not wishing to force restart anything, while apt-get might be in the middle of installing stuff, I went away for 1/2 an hour or so. Came back, and I could still hear the film going ... but it was jerking, the audio was cutting in and out, as though mplayer were having difficulty buffering. And I could the hard drive whirring like it was about to emit smoke.  

Waited a little longer, then pressed ctrl + alt + backspace. There was no response so I pressed the force restart on the box.

When the box restarted, it started emitting the machine gun beep noise you get when you hold a button down on the keyboard. Then it refused to boot, saying "No keyboard, or non system keyboard present".

Unplugged the box, jiggled the keyboard usb cable a bit at the back. Plugged it back in. This time the system didn't post, and all I got was one long beep, followed to short ones. 

Unplugged it again, removed the keyboard usb plug from the box, and switched it on again. This time it posted, and got as far as "No keyboard, or non system keyboard present" error. 

Re inserted keyboard plug, then pressed restart button again. This time it all booted up, apparantly normally.

Two questions:

(1) WTF just happened?

(2) Having force restarted it, should I run some sort of disk check utility on my partitions? If so, what should I use?

---

