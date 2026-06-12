---
title: "PLEASE HELP - Stupid 5.1 problem and no advices... almost ready to give up."
date: 2005-10-31
forum: Desktop Environments
---

### Post by Chareos on 2005-10-31
I'm facing a very stupid problem with my 5.1 setup on nforce audio:

rear right channel is mute, and I suspect that center channel is being played over another one.

note that "speaker-test -Dplug:surround51 -c6" gives excellent and perfect working results, every channel on the right speaker.

No matters what media player I try, every 5.1 track on dvd or avi files suffers from this problem.


I just want to have 5.1 working as in hoary (anyone has an asound to share ?) and dmix for multiple streams... I have no way to study the entire bloat alsa system.


Can anyone help me ?

---

### Post by SlowJet on 2005-10-31
see this 

 [http://www.linuxquestions.org/questions/archive/18/2004/04/1/122943](http://www.linuxquestions.org/questions/archive/18/2004/04/1/122943) 

Down a ways it saying nForce doesn't support software mixing (or it is the mixer program)

Is that what dmix is?

SJ

---

### Post by JLB on 2005-10-31
[http://www.nforcershq.com/forum/nforce-linux-vf29.html](http://www.nforcershq.com/forum/nforce-linux-vf29.html)

Have you tried this place yet? I briefly looked and folks have their asound configs posted.

---

### Post by Chareos on 2005-11-01
Tinkerng a lot I got this .asoundrc file:

pcm.dmix51 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0666
slave {
pcm "hw:1,0"
channels 6
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
}

ctl.dmix51 {
type hw
card 1
}

pcm.stereo {
type plug
slave.pcm "dmix51"
ttable.0.0 1
ttable.1.1 1
}

pcm.!default {
type route
slave.pcm "dmix51"
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.4 1
ttable.0.5 1
ttable.1.5 1
}

pcm.duplicate {
type plug
slave.pcm "dmix51"
slave.channels 6
route_policy duplicate
}

which let me hear 4.1 sound in xine (specifying plug:dmix51 as devices).

Now I cannot get VOICES !

On central speaker there's probably the sum of front left and right speakers.
Anyway I assume this is a routing problem, not a dmix one.


Any other suggestion ?

---

### Post by Chareos on 2005-11-01
OH MY GOD !

I tried mplayer instead of xine... and works !!

Now... I hope to find the way to manage dvd menus with mplayer...
(sigh, remote control to reconfigure from scratch... WHY xine turned out to be my traitor ?)

---

