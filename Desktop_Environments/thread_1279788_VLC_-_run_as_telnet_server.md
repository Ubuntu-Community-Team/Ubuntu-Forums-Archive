---
title: "VLC - run as telnet server?"
date: 2009-10-01
forum: Desktop Environments
---

### Post by dchurch24 on 2009-10-01
Hi,

I've been developing a complete 'home automation/entertainment' system for a few months now, and having got the doors lights etc... all wired up and working through touchscreens/phone/Internet etc... I've got to the point where I am trying to implement my 'whole house audio' part of the system.

So far I have a telnet server (written by me in c#/gtk#) that checks a centralised 'playlist' (mysql), when there is something to play it stops listening and plays. When the process ends, it asks for another song to play and if that song should be played by itself (each entry in the playlist has a room number next to it to determine which room (or listener) should play it), if there's anything in the playlist it shells VLC and plays the next one in sequence.

However, while developing this I have run across websites claiming that VLC can run as a telnet server.

Is it possible to telnet into VLC and remotely tell it which song/movie file to play? Would it return a code of some sort when it's finished playing?

---

### Post by Ropetin on 2009-10-01
I hate to just post a link, but;

[http://www.videolan.org/doc/streaming-howto/en/ch05.html]("http://www.videolan.org/doc/streaming-howto/en/ch05.html")

---

### Post by Scythium on 2009-10-01
I was thinking of doing something similar in my house, I would love to see a video of your hard work. It sounds so cool!

---

### Post by dchurch24 on 2009-10-02
Fantastic! Thank you very much.

---

### Post by dchurch24 on 2009-10-11
> **Scythium said:**
> I was thinking of doing something similar in my house, I would love to see a video of your hard work. It sounds so cool!

Hi,

Sadly, the machine that conrols the lights etc... had it's HDD go on Friday, so I'm just putting a new one together.

I decided not to use VLC in the end, instead I wrote the front end using Mono/SDL.Net. It plays the songs itself so that problem is solved now.

I will send a PM with a link to a vid when I get it all up and running again (it might be sooner than I think, we have guests for dinner later and I'm hoping to get it all up and running before then!)

---

