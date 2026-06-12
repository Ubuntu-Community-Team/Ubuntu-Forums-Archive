---
title: "GFCEU Freezes System; Debug Mode Stutters"
date: 2010-03-09
forum: Gaming &amp; Leisure
---

### Post by Groucho Marxist on 2010-03-09
I'm attempting to use GNOME FCE Ultra 0.6.1 in 64-bit Ubuntu 9.10. However, when I start up the program, it freezes and commits 100% of one of my dual-core processors to the process. The strange part is that when I boot up gfceux (which displays as GFCE UltraX 2.2svn), I can use the program until it starts stuttering and freezes up altogether.

Has anyone else had these problems and knows how to resolve them?

---

### Post by Groucho Marxist on 2010-03-10
Bump

Problem continues to plague my system.

---

### Post by Groucho Marxist on 2010-03-12
Bump for the power up to win the game

---

### Post by UltimusRex on 2010-03-14
I'm having the same issue. It's an audio problem. Disable audio in the settings and it will probably work. That fixed it for me.

Though this is not a fix for me. What's the fun of playing with no audio? So I'm still waiting for someone who knows more than I do to suggest an actual solution to the problem. It seems like every emulator has audio issues with Ubuntu. Another solution for me would be if someone could suggest another easy to install NES emulator that doesn't generally have the audio problems.

---

### Post by Groucho Marxist on 2010-03-14
> **UltimusRex said:**
> I'm having the same issue. It's an audio problem. Disable audio in the settings and it will probably work. That fixed it for me.

Though this is not a fix for me. What's the fun of playing with no audio? So I'm still waiting for someone who knows more than I do to suggest an actual solution to the problem. It seems like every emulator has audio issues with Ubuntu. Another solution for me would be if someone could suggest another easy to install NES emulator that doesn't generally have the audio problems.

I agree; sound either works, then crashes, or the program works perfectly sans audio. 
When I get home from work, I'm going to test out GFCEU with my controller to see if this temporary solution to a long-term problem works. My thanks either way for the help :)

I'll post the results of whatever occurs ASAP :)

---

### Post by Groucho Marxist on 2010-03-14
Just finished playing a game at home; the graphics still stutter after disabling audio but nothing is moving in slow motion any more.

Can anyone here aid us in fixing this problem?

---

### Post by punkrockguy318 on 2010-03-18
Hey ubuntuforums

I'm one of the head FCE ultra devs and I spend most of my time on the linux port

i'd really like to get these problems resolved


i'm on vacation so I sort of skimmed the thread, but this is a seiruos concern for me.  I will look into this when I get back, but please leave a bug in the SF bugtracker for fceux [http://fceux.com](http://fceux.com)

you can alaso email me directly but the tracker is great : LTsmooth42 @ gmail.com

in the mean time, try doing this before you run fceux:

export SDL_AUDIODRIVER=esd

even if you're not using esd; the esd drivers works MUCH better than the pulse one (even when using pulseaudio server)

sorry i can't go into more details right now; i'm in the cariibean!  but yes someoen please email me or report aa bug because i will forget about this by the time I return home

---

### Post by punkrockguy318 on 2010-03-18
> **Groucho Marxist said:**
> Just finished playing a game at home; the graphics still stutter after disabling audio but nothing is moving in slow motion any more.

Can anyone here aid us in fixing this problem?

sound is one of the main reasons I play NES (i love 8 bit music) so the issue is being taken very seriously.

i'm going to do what i can when I get back to get this resolved

game on:popcorn:

---

