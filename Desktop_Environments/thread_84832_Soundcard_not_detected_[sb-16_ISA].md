---
title: "Soundcard not detected [sb-16 ISA]"
date: 2005-11-01
forum: Desktop Environments
---

### Post by mackinax on 2005-11-01
I've searched and read many threads but can't find a solution. I am running Ubuntu 5.10 'Breezy Badger', and the problem is my sound card wasn't detected. It's a Creative SoundBlaster 16, model# CT4170, ISA slot.

And, of course, I don't have a lot of linux experience.

Thank you!

Mackinac


edit: Per advice in a thread I found in these forums, I added the line ***sb io=0x220 irq=5 dma=1 dma16=3*** to /etc/modules. It didn't help... the Sound Preferences dialog still shows nothing to select under "Default sound card:"

---

### Post by Teroedni on 2005-11-01
It is possible to get it working, but it is a lot of working and very difficult
You have to compile unfortunally
[http://hardware.linuxfaqs.de/view.php?tab=cards&ctype=Sound](http://hardware.linuxfaqs.de/view.php?tab=cards&ctype=Sound)
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Soundblaster-AWE.html#ss2.2](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Soundblaster-AWE.html#ss2.2)

---

### Post by Teroedni on 2005-11-01
Is there someone who could help him/her with regards to the compile?
I am a noob here:(

---

### Post by mackinax on 2005-11-01
As in recompile the kernel? :shock: Naw... it couldn't be that bad... I hope. I've never had to do anything so drastic with other distros i've tried.

---

### Post by Teroedni on 2005-11-01
I am afraid you have to

i will see if i find other methods but i doubt it

Please if anybody knows about this :confused:

---

### Post by Teroedni on 2005-11-01
ahh here is something
Maybe you dont need to compile
[http://www.linux.ie/newusers/beginners-linux-guide/awe-setup.php](http://www.linux.ie/newusers/beginners-linux-guide/awe-setup.php)

try it :)

---

### Post by mackinax on 2005-11-01
I found a solution! 

following a lead from [this thread]("http://ubuntuforums.org/showthread.php?t=1805&page=2"), I went to /lib/modules/2.6.12-9-386/kernel/sound/isa/sb/ and found snd-sb16.ko there .... so I changed that line I previously added in /etc/modules to:

**snd-sb16 io=0x220 irq=5 dma=1 dma16=3**

... then rebooted, and now my sound is working!  :D

---

