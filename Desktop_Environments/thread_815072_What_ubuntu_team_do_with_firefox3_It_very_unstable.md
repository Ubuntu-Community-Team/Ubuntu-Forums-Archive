---
title: "What ubuntu team do with firefox3? It very unstable!"
date: 2008-06-01
forum: Desktop Environments
---

### Post by Ilya Skorik on 2008-06-01
Dear Ubunt team, i'm use ubuntu last three years, and also was very happy, but now I wish to ask my first question, what happens with ubuntu?

I shall explain on a small example:

On my computer standart firefox3 from ubuntu repo with flash-nonfree plugin crash on 20 times per day! I suspect, that the problem is connected with adobe flash player 9 and pulse audio. 

After installation of flash 10 beta firefox began to crash 5-10 times a day. It's mutch better.

Very often firefox is simply closed without an explanation of the crash reasons. Sometimes it hangs, freezing the window. Quite often it creates zombie process which cannot be terminated.

But after I have install firefox from a mozilla site (original), it crash only time-two for a day!

Please, tell, you subject to what awful mockeries firefox before to include it in ubuntu repo?

Including other defects connected with pulse audio and periodic restarts of xorg(with comiz, when I disable compiz all work fine) I start to think, that 8.04 LTS it is necessary to rename in 8.04 LCG - Long &#1057;orrection of Bugs.

I have very standard hardware, athlon xp, nvidia 7900, etc. And use standart ubuntu repos.

And second question - it is possible to trace the reasons of firefox crashing? I can't create bugreport because I don't know why it's happens.

---

### Post by Zorael on 2008-06-02
This is mostly due to Flash which is proprietary, so developers can't do much about it beyond helping send in bug reports to Adobe themselves. There is a way of getting it to stop crashing the browser (by wrapping it with **nspluginwrapper**, search the forums for that), but Flash will still eventually bug out, and to recover from that you either need to close all tabs containing flash content or restart the browser completely.

If you start firefox from a terminal, it will output error messages there as they occur.

My suggestion would be to leave FF3b5 alone for the time being and revert to FF2, Swiftweasel2, Konqueror, Epiphany, Opera, or whatever other browser you may prefer. I suggest Swiftweasel, since it's based on Firefox and further optimized to be faster. See [http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/).

> **Wikipedia][SIZE="4"]Optimization[/SIZE]

Swiftweasel is optimized using the following methods:

**Binary code optimization**
[list]
    [*] Compiled with options that optimize for speed rather than binary size.[list]
          [*] Swiftweasel is compiled -O3, (the highest level)[list]
                [*] The resulting Swiftweasel binary is larger than Firefox.[/list]
          [*] Firefox is compiled -Os (which is for binary size).[/list]
    [*] Binaries incorporate additional instruction sets.[list]
          [*] Intel and AMD: SSE, SSE2, SSE3, and MMX.
          [*] AMD only: 3DNow![/list]
    [*] Optimization specific to the build microprocessor architecture.[list]
          [*] Intel 32bit: Pentium 4, Pentium 3, Pentium M, Pentium 3M, Pentium 2, Prescott.
          [*] Intel 64bit: Nocona
          [*] AMD: Athlon XP, Athlon, K6-2, Athlon.
          [*] AMD64: Athlon64, Opteron[/list]
    [*] Compiled with newer version of GCC (Firefox 2.0 uses 3.3.2, Swiftweasel 2.0 uses 4.0.3).[/list]

**Increased Security**[list]
    [*] Better protection from Buffer overflow attacks (Swiftweasel 2.0 uses -D_FORTIFY_SOURCE=2 said:**
> 

**Simplify**[list]
    [*] IPv6 DNS lookups are disabled, preventing slowdowns 
    [*] HTTP pipelining is enabled by default. Note that Fasterfox provides a GUI to adjust these settings.
    [*] For full details, users can download source packages with all changes listed.[/list]
Lastly, LTS does not mean that the distro is guaranteed to be completely bug-free. In a few months, FF3 and PulseAudio may very well be the de facto standards, and if Hardy were to have FF2 and plain ALSA (boo! [OSS4!](http://tinyurl.com/5c6luu) :>), it'd be considerably out-of-date.

---

### Post by Sef on 2008-06-02
> Lastly, LTS does not mean that the distro is guaranteed to be completely bug-free.

Yes, that is true.  LTS = Long Term Support.

> Please, tell, you subject to what awful mockeries firefox before to include it in ubuntu repo?

Support for Firefox 2 will run out in December 2008, while support for Ubuntu Hardy will run until April 2011.

---

