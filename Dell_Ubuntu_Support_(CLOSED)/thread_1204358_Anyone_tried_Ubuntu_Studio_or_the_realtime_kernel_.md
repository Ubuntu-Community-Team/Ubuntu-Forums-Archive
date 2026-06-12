---
title: "Anyone tried Ubuntu Studio or the realtime kernel on a Dell mini?"
date: 2009-07-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nunu_ubu on 2009-07-04
I am running Hardy (pretty sure the Netbook version) on a Dell mini 10, with Intel Atom processor.  Pretty new to ubuntu.  I'm also a beginning bass guitar player and would like to get into DJ'ing.  I realize minis aren't made to be high end media production machines, but I don't really want to do anything high end (at least, I don't THINK it's high end... Could be wrong.  Don't really know what kind of processing power is needed to do what I want).

Here's what I want to do with my mini:
- Make drum loops (preferbly with H2) to practice playing bass with.
- Have a program(s) that I can DJ with, that will allow me to fade songs together (that preferbly keeps the beat in synch so I don't train wreck, though doing this manually is no big deal) in real time, remix songs, pick apart songs and splice them together (such as pulling the bass line out of one song, and adding the guitar track out of another song), and be able to loop song(s) and parts of songs in real time (such as letting the intro play, then make a verse loop 4 times, then continue the song - in jargon, make a start-loop point and an end-loop point)
- create, edit, play, and loop midis without a time delay
- be able to listen to music, watch movies, write documents, and use the internet

Having super awesome quality audio is not a concern, just as long as it isn't glitchy and clicky - don't need USB-to-speaker support, my 1/8" stereo headphone out is good enough.  I do realize getting a more powerful machine would be better, but that's something for the future when I can afford it and I'm more comfortable in my ability to do the aforementioned things.

I've tried installing the individual programs (such as Hydrogen) and using them.  I can make patterns fine, but the sound is glitchy.  To cut this short... I've been on this "get suggested packages to make other packages work" binge, and I'm starting to run into compatibility issues.  For instance, I installed JACK, but for some reason everything that runs on ALSA stopped working - Amarok kept giving me an error whenever I tried to open it, and Timidity and H2 had no sound.  So I just uninstalled JACK.  I don't have the error screens.  So I started looking into the realtime kernel, thinking that might help - but I have no idea how to install it.  It doesn't show up in my Synaptic, nor does apt-get install find any of the packages various sites say are out there.  (again... very new to ubuntu.  Could be missing some vital steps).  I tried doing all this instead of immediately installing Studio, as I kept seeing headlines on how Dell's systems are kind of a stand alone deal, and it would be who of me to stick with what they provide.

So that brought me back to Studio. Has anyone tried running Ubuntu Studio on their Dell mini?  Would it be who of me to stick with Hardy Studio, or just go ahead and get Jaunty Studio?  If Studio is too much for my netbook, any suggestions on how to clean up my system so I can closer to what I want to do?  Any help will be greatly appreciated!

:guitar:

---

### Post by mikewhatever on 2009-07-04
I really doubt an Atom CPU can handle Ubuntu studio. As for rt kernels, they are in the repositories. Could it be that you aren't looking for the right name?
[linux-image-2.6.28-3-rt]("http://packages.ubuntu.com/jaunty/linux-image-2.6.28-3-rt")
[linux-image-2.6.24-18-rt]("http://packages.ubuntu.com/hardy/linux-image-2.6.24-18-rt")

---

### Post by nunu_ubu on 2009-07-14
Thanks Mike!

I only get to get on the next once a week or so, and I'm glad I got at least one reply.

I don't believe i tried those files, when using the terminal.  I kept looking in Synaptic, but didn't see anything with rt.

I finally finished downloading Studio 9.04 iso.  I'm going to put it on an SD card and install it on a 40 gig partition on my mini, and see what happens.  See what I can tweek or downtune to work better with what I got.

I've got some questions about doing that before I do it, but I'm going to post those in a new thread.

---

### Post by mikewhatever on 2009-07-14
You are welcome. It's been a week and I gained some experience with my own mini 10 (z530 cpu), which supports the initial skepticism. UNR was barely usable with interface lagging badly. Ubuntu proper worked ok, but was lacking in multitasking and video, the netbook was also getting very warm. I ended up installing the base system with LXDE, which works quite well (flash, skype, video/audio). That said, I am all for trying out Ubuntu studio. Post an update when you are done.

---

