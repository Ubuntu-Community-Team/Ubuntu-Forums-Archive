---
title: "How I fixed &quot;Couldn't open SDL audio: No available audio device&quot; with Quake 2"
date: 2005-10-25
forum: Gaming &amp; Leisure
---

### Post by Staesys on 2005-10-25
I thought this would help someone, so here it is. This also works for Cube too, btw...

I installed the game with the native Loki installer and then copied my /baseq2/ files from my XP machine.

[http://www.liflg.org/?catid=6&gameid=55]("http://www.liflg.org/?catid=6&gameid=55")

The first problem it had was it would only run in software mode, the second problem was the lack of sound. The software rendering issue was resolved after I created a quake2.conf file in the /etc/ folder, thanks to a marvelous HOW TO page I found.

[http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html]("http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html")

The sound problem however eluded me, until I found a post somewhere on this forum with the solution. Basically, you create a script and save it in the /usr/bin/ folder and chmod +x it to make it executable. I cannot for the life of me find this post again or I'd post the URL to give credit to this person.

Here's the script:

```
SDL_DSP_NOSELECT='1'; export SDL_DSP_NOSELECT; quake2
```

I named it q2sound. Now all I have to do is run this script and I can play Quake 2 in glorious stereo. (hehehe)

I'm running it in 1024x768 and it's as smooth as a babies butt!

---

### Post by daller on 2005-11-14
Nice...

---

