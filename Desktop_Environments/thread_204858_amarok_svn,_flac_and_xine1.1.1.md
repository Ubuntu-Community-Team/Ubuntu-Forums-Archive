---
title: "amarok svn, flac and xine1.1.1"
date: 2006-06-27
forum: Desktop Environments
---

### Post by fanoodlehey on 2006-06-27
I can't work out where to post this so feel free to tell me to move somewhere else.

I use the svn version of Amarok. It's the only app that I keep above the level of what's in the repositories. After my last update I couldn't play flac encoded tunes. After some talking on the amarok IRC it turns out the problem is a bug in xine1.1.1 which I use as my engine.

Hopefully xine 1.1.2 will be backported to Dapper once it is released and included in Edgy.

In the mean time. How do I go about patching the bug? Any pointers would be helpful.

Thanks.

---

### Post by Podex on 2006-06-30
Apparently there is a fix, in which you need to change a file from the xine source and compile. [http://sources.gentoo.org/viewcvs.py/gentoo/src/patchsets/xine-lib/1.1.2cvs20060328/270_all_flac-has-audio.patch?rev=1.1&view=markup](http://sources.gentoo.org/viewcvs.py/gentoo/src/patchsets/xine-lib/1.1.2cvs20060328/270_all_flac-has-audio.patch?rev=1.1&view=markup)

I tried it, but it didn't work. Maybe I did something wrong, but Im not going to try again, since I'm afraid I&#314;l break something :)

---

### Post by fanoodlehey on 2006-06-30
How do you even try to implement this fix. I have no idea how this works but I'm willing to try.

---

### Post by citizenkeith on 2006-07-02
[QUOTE=fanoodlehey]How do you even try to implement this fix. I have no idea how this works but I'm willing to try.[/QUOTE]


Me too. Anybody?

---

### Post by Podex on 2006-07-04
Well you need to go to your xine 1.1.1 source (or get it) and change src/demuxers/demux_flac.c as said in [http://sources.gentoo.org/viewcvs.py/gentoo/src/patchsets/xine-lib/1.1.2cvs20060328/270_all_flac-has-audio.patch?rev=1.1&view=markup](http://sources.gentoo.org/viewcvs.py/gentoo/src/patchsets/xine-lib/1.1.2cvs20060328/270_all_flac-has-audio.patch?rev=1.1&view=markup) and then recompile.
Or get the latest 1.1.2 cvs which has it fixed: [http://sourceforge.net/cvs/?group_id=9655](http://sourceforge.net/cvs/?group_id=9655)
Or wait for a 1.1.2 package as I'm doing :S cause compiling the cvs isn't working for me.

---

### Post by fanoodlehey on 2006-07-17
Thanks. I think I'll wait for the 1.1.2 version to see what happens. 

I'm using Amarok 1.4.0 at the mo' but I'm really looking forward to the improved last.fm support on 1.4.1. I think this is the area where Amarok is really going to start to excell as it moves towards Amarok 2. Good use of the data available on last.fm and a slick interface to it will make Amarok a truely outstanding music player.

---

