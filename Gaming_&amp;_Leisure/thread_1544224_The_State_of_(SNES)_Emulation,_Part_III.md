---
title: "The State of (SNES) Emulation, Part III"
date: 2010-08-02
forum: Gaming &amp; Leisure
---

### Post by dfreer on 2010-08-02
[quote=byuu]Work is going well here, too. blargg put a lot of research into the S-SMP TEST register. We now have six of the eight bits 100% perfectly emulated, even down to the ability of certain frequency settings to permanently deadlock the processor due to bus conflicts with the S-DSP sharing the APURAM.[/quote]

Great to see that SNES emulation is still going strong, and almost completely accurate now too. Now if only N64 and the Playstation emulation would resume making progress :(

As for bsnes, byuu also claims:
[quote=byuu]Seeing that I can now get 45fps even on the lowest-end Intel Atom netbook processors, and over 200fps on top-of-the-line Intel Core processors, is a very encouraging sign as well. Within the next decade, I believe it will be possible to run bsnes even on handheld and portable hardware, such as cell phones.[/quote]

Seeing as byuu as the tendency to overestimate his goals (I believe that save state support was "never going to happen" and then in about 1 week *poof* it was implemented), I would love to think that 60fps on Intel Atom would be possible in the next year. But that's just me :D

[Full Article Link](http://byuu.org/articles/emulation-3)
[Download BSNES Source](http://byuu.org/bsnes/)
[Compilation Guide](http://byuu.org/bsnes/compilation-guide)
[Forum Thread for Compiling on Ubuntu](http://board.byuu.org/viewtopic.php?f=3&t=772&start=0)
[Unofficial .deb Repository](https://launchpad.net/~hunter-kaller/+archive/ppa)

---

### Post by Åtta on 2010-08-02
Nice to see that they're making headway, but honestly, Zsnes has been working just fine for the last... 9 years? I know it's not even close to being as accurate, but from purely a gamer's perspective - I don't really care.

What I would like to see is better support for Nintendo 64 emulation. Mupen64plus is slowly getting there, but it's still far, far from being complete. I have yet to find a game that runs without any kind of flaw.

EDIT: OHNOWWAITAMINUTE! I'm reading the full article, and I happened to notice this: "Mednafen has added the bsnes core for its SNES emulation, which allows for **netplay support**." Me likey! Will now switch to bsnes, if my laptop is fast enough.

---

### Post by dfreer on 2010-08-02
> **Åtta said:**
> Nice to see that they're making headway, but honestly, Zsnes has been working just fine for the last... 9 years? I know it's not even close to being as accurate, but from purely a gamer's perspective - I don't really care.

What I would like to see is better support for Nintendo 64 emulation. Mupen64plus is slowly getting there, but it's still far, far from being complete. I have yet to find a game that runs without any kind of flaw.

EDIT: OHNOWWAITAMINUTE! I'm reading the full article, and I happened to notice this: "Mednafen has added the bsnes core for its SNES emulation, which allows for **netplay support**." Me likey! Will now switch to bsnes, if my laptop is fast enough.

I haven't gotten to try the netplay in mednafan myself, from what I understand of it it's pretty basic. In Windows it's also command-line only.

---

### Post by tukuyomi on 2010-08-29
> **Åtta said:**
> Will now switch to bsnes, if my laptop is fast enough.
Want to try the Performance core from bsnes v068?
Get the flavor you want:
[http://tukuyomi.kuro-hitsuji.net/stuff/bsnes/bsnes_v068/pgo/](http://tukuyomi.kuro-hitsuji.net/stuff/bsnes/bsnes_v068/pgo/)
From the bsnes Settings, choose Performance core and restart the emulator :)

---

### Post by hikaricore on 2010-08-29
I'm still fine with zsnes tbh, I've been using it for about 12 years and it's never let me down.

---

### Post by byuu on 2010-08-31
I don't follow. If you're happy and dead-set on what you're using, then nothing I ever do would convince you to try something new. So why do you mention that you're not interested on every thread here? It does not seem to add anything of importance to the conversation.

Are you a person of particular importance that others look to for advice? It would seem prudent in that case to list some positives of ZSNES over bsnes, so others can make an informed decision. Or is there is some killer feature that you are wanting in an SNES emulator that may change your mind about trying alternatives? I am open to suggestions if that is the case.

No disrespect intended.

---

### Post by slave-zeo on 2010-09-02
I used to use ZSNES but since I got my new computer I switched to BSNES. Although I cant really tell the difference between the two playing a game.

A lot of the reason why people do not use BSNES is because of it's insanely high system requirements. Whereas ZSNES will run on my toaster with upgraded ram.

I do like BSNES's interface a little better, it fits in with my desktop a little more, it looks more like a desktop app. Although when you load up ZSNES it's interface screams "PLAY ME, I'M FUN!".

---

### Post by hikaricore on 2010-09-02
> **byuu said:**
> Are you a person of particular importance that others look to for advice?

Bingo

---

### Post by tukuyomi on 2010-09-02
> **slave-zeo said:**
> people do not use BSNES is because of it's insanely high system requirementsNot anymore :) -see my previous post on this thread^^-
[http://img641.imageshack.us/img641/6418/bsnesv067r10.png](http://img641.imageshack.us/img641/6418/bsnesv067r10.png)
(more infos on byuu.org -news from 2010-08-10-)

---

### Post by slave-zeo on 2010-09-02
> **tukuyomi said:**
> Not anymore :) -see my previous post on this thread^^-
[http://img641.imageshack.us/img641/6418/bsnesv067r10.png](http://img641.imageshack.us/img641/6418/bsnesv067r10.png)
(more infos on byuu.org -news from 2010-08-10-)

Yeah yeah yeah performance setting :) BSNES still has the stigma of being a resource hog. I use BSNES though and have no complaints.

---

### Post by byuu on 2010-09-05
> **hikaricore said:**
> Bingo

I see, thank you. So why in that case are you not providing any useful information? I know if people were looking to me for advice I would want to provide context. Absolutely nothing is perfect and every emulator has various tradeoffs.

Perhaps I should point out why your argument is not persuasive in a way that affects something you presumably care about:

(Pretend thread recommending someone try out Ubuntu)
> I'm still fine with debian tbh, I've been using it for about 12 years and it's never let me down.I'll give you an example for the next time you recommend software to others. Note the lack of bias, that one's very important.

Advantages and unique features of bsnes:
- 100% compatibility rate, no known bugs, no game specific hacks
- Super Game Boy emulation
- 7-zip and multi-archive support
- internal cheat code database, no need to Google for codes
- support for various things like UPS, XML mapping, MSU1, serial comm, etc
- [for hackers] a debugger

Disadvantages and missing features of bsnes:
- higher system requirements rule out systems slower than netbooks
- will always be the worst choice when running on battery power
- netplay requires Mednafen/bsnes, the official GUI lacks it
- lacks input macros (as in ZSNES) and re-recording (as in Snes9X-rr)

Problems that can and do affect all emulators:
- video, audio and input driver issues (no one driver can work on all hardware)
- Vsync and Async issues (see above)
- ease of use (highly subjective to personal tastes)

See? Now people can make an informed opinion.

---

### Post by hikaricore on 2010-09-05
People also have a tendancy to take me way too seriously. ;)

---

### Post by Mike'sHardLinux on 2010-09-05
> **hikaricore said:**
> People also have a tendancy to take me way too seriously. ;)

Maybe it's 'cause your bean count? :confused:

---

