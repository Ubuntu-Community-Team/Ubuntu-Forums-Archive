---
title: "Skype chews 100% cpu while sitting idle"
date: 2009-05-04
forum: General Help
---

### Post by epswing on 2009-05-04
I've recently upgraded to 9.04 from 8.10, and Skype, while it connects fine, I can make calls through it, etc, will suck up 100% of one of my cores after sitting idle for a few minutes.

I've reinstalled Skype but I'm facing the same problem.

Any hints?

---

### Post by garythegoth on 2009-05-04
> **epswing said:**
> I've recently upgraded to 9.04 from 8.10, and Skype, while it connects fine, I can make calls through it, etc, will suck up 100% of one of my cores after sitting idle for a few minutes.

I've reinstalled Skype but I'm facing the same problem.

Any hints?

CPU type?

---

### Post by soro2005 on 2009-05-04
I bet you use pulseaudio as output. [Here's your bug report](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203). I've found that the pulseaudio alsa plugin sometimes hangs on skype events that throw a sound. Perhaps the problem can be prevented by disabling some of the notification sounds.

---

### Post by garythegoth on 2009-05-04
> **soro2005 said:**
> I bet you use pulseaudio as output. [Here's your bug report]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203"). I've found that the pulseaudio alsa plugin sometimes hangs on skype events that throw a sound. Perhaps the problem can be prevented by disabling some of the notification sounds.

Pulseaudio......

---

### Post by epswing on 2009-05-04
> **garythegoth said:**
> CPU type?

Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz

---

### Post by soro2005 on 2009-05-05
I have found that I can terminate a hanging audio stream by occasioning a new one. CPU high --> Send a smiley to somebody --> pipe unclogged and CPU ok again. Of course, you need to explain to that somebody why he or she is getting unmotivated smileys. :guitar:

---

### Post by epswing on 2009-05-05
So what does one do in these situations?  Wait for a new version of skype?  Wait for a ubuntu update?

---

### Post by soro2005 on 2009-05-06
> **epswing said:**
> So what does one do in these situations?  Wait for a new version of skype?  Wait for a ubuntu update?

It's probably in the alsa plugin that Skype (and some other programs) use to communicate with pulse audio. The alsa plugin is being maintained. If you want to try, you might be able to track down something in the alsa bug tracker, or somebody to look into it from that end. Probably, they are already aware of the issue.

Meanwhile, your best bet is to wait for a new Skype with improved sound support, [which seems to be in the making]("http://share.skype.com/sites/linux/2009/01/skype_for_linux_updates.html"). Or you can use alternatives, such as amsn or ekiga.

I currently find it quite manageable here. I have enough cpu power to live with the high consumption during conversations, and I'm working on my procedure for shooting down hanging sound streams without having to log out of Gnome. My current procedure: Look into the Pulse Audio volume control to see what streams using the alsa plugin are currently registered, quit all programs that have one, other than Skype (Flash player, for instance), then send a sound event in Skype to unclogg the pipe. A smiley to a friend normally does the job. CPU down, Pulse audio still up, Skype ready to go. Not ideal, but okay.

---

