---
title: "Poor Performance of CS:S"
date: 2005-10-10
forum: Gaming &amp; Leisure
---

### Post by bugmenot on 2005-10-10
Hi, I jus tried playing CS:S for the first time on P2P and it was soooo slow, can someone explain why? I have a celeron 2.5, FX 5500, and 768 RAM.. it ran just fine in windows and I installed the nVidia drivers correctly in my Ubuntu.
The reason I'm asking this here is because I doubt I'll get an answer off transgaming

---

### Post by seethru on 2005-10-10
how slow is slow? What graphics settings do you have turned on in P2P and in CS:S?

---

### Post by bugmenot on 2005-10-10
I'm not sure in P2P, haven't played with P2P yet, just woke up in the morning to see how CS:S did in the stress test. It felt like it was skipping 20 frames every second. The graphics were on high, but shader and shadows were on low. And DX was set on 8.0 of course. :confused: 15 dollars, Microsoft, and games gone. For all other things: Linux :D

---

### Post by seethru on 2005-10-10
the reason you're probably feeling the slow speeds then is because you haven't told P2P how much graphics memory you have, or the AGP Vertex data size. Either edit the default profile, or make a new one for Steam and specify video memory, and agp vertex data size.

---

### Post by bugmenot on 2005-10-10
How do I know how much vertex memory I have.. and my card is PCI, do I still need to have it enabled?

---

### Post by seethru on 2005-10-10
no, you shouldn't need the vertex memory then

---

### Post by bugmenot on 2005-10-10
Well I was playing around wiht the settings and NONE of them made any difference.. I think it's because it's not applying them to the game itself but only to the steam interface

---

### Post by seethru on 2005-10-10
no, it applies to CS:S also. Since you have an older card I'd try disabling vertex and pixel shaders in P2P, see if that makes a difference.

---

### Post by bugmenot on 2005-10-10
I just did that. 20 fps in stress... ?

---

### Post by seethru on 2005-10-10
try just playing a game and see how that goes, and report back if you experience slow performance.

---

### Post by bugmenot on 2005-10-10
You mean CS:S itself? I did lol very bad performance, unplayable. I really feel like my drivers are no installed, not just because of CS:S, but because Ubuntu feels very choppy. But they are installed. I get 21xx fps in glxgears, I have the nvidia logo when gnome starts, and glxinfo says nvidia..

---

### Post by seethru on 2005-10-10
what kind of performance do you get in windows? Are you using the same settings in linux that you did in Windows?

hehe running out of options here hehe

---

### Post by bugmenot on 2005-10-10
I got 50 fps in stress test, no slow downs. I'm not sure what you mean about same settings? I didn't use P2P in windows and windows doesn't have any settings simillar to Linux

---

### Post by seethru on 2005-10-10
I mean in the actual game, like same resolution? etc etc..

---

### Post by bugmenot on 2005-10-10
Yes, same res as desktop, same bad performance

---

### Post by seethru on 2005-10-10
hmm, can you go through what P2P video options you have on, and what they're set to? Also what have you set pthreads to?

edit: you've installed the nvidia-glx package right?

---

### Post by bugmenot on 2005-10-10
Pthreads: right now it's on ON but it makes no difference when it's on default. I'll tell you what I have different from default: Decrease wineserver is unchecked, audio ALSA, Video RAM 256, unchcked vertex shader,  nv_var, arb_vbo, pixel shader is checked because it made no difference with it on and off and i read it gives a little performance boost on 8.0. Yes I have nvidia-glx installed

---

### Post by seethru on 2005-10-10
hmmm, I'll compare those to what I have at home, I've got a 6800GT so the options I have turned on will have to be set lower than what you have.

Try setting that vertex option on btw.

Also, since you did say you're using a PCI card that could be why, I did note you used an ATI card in another post, so you MAY want to try that but thats up to you, because it is known that ATI's *nix support is HORRIBLE.

---

### Post by bugmenot on 2005-10-10
That's what I heard. I get more fps in glxgears (yes yes not a benchmark blah blah) with my nvidia, but slightly better performance better in ut2k4 with the ATi, but no way I'm gonna install ATi again, I'll also have to reinstall Ubuntu (never again, 7th in 3 days isn't going to happen) so that I'll be sure everything nvidia is removed.. I wish I could get 66's to work, I'm sure I'll get about 10 extra fps. Artificial Intellegence has a nitro kernel 2.xxx or something+66's optimized gaming coputer and I PMed him about it but he hasn't answered

---

### Post by seethru on 2005-10-10
yeah...if your performance was worse with the nvidia I'd say the PCI is the bottleneck then.

---

### Post by bugmenot on 2005-10-10
it can't be a bottleneck. The rest of my system is as bad as the card itself: celeron 2.5, 768 ram, but don't blame it on my system, like i said css ran fine on windows. %60+ lower performance? I can't believe i threw windows out for this :(

---

### Post by seethru on 2005-10-10
not much else we can do, aside from you retrying your ATI with css instead of ut2k4. Blame it on ATI for not giving proper support to Linux.

You can't expect it to perform exactly the same in Cedega, it is emulation.

---

