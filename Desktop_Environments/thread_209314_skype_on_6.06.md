---
title: "skype on 6.06"
date: 2006-07-04
forum: Desktop Environments
---

### Post by mosestruong on 2006-07-04
Has anyone been able to get skype to work in 6.06?

I've followed the instructions in the ubuntuguide, but when I start, i get an error:

*** glibc detected *** free(): invalid pointer: 0x08a1e1c8 ***
Aborted

I've tried to follow the thread [http://www.ubuntuforums.org/showthread.php?t=171761](http://www.ubuntuforums.org/showthread.php?t=171761) and install skype-dsp-hijacker, but the problem still exists... now I get

hijacker: skype_dsp_hijacker v0.6
hijacker: when Skype opens DSP /dev/dsp
hijacker: - microphone used: /dev/dsp
hijacker: - speakers used:   /dev/dsp
hijacker: when Skype opens mixer /dev/mixer
hijacker: - mixer used: /dev/mixer
*** glibc detected *** free(): invalid pointer: 0x08a1ef38 ***
Aborted

anyone know how I can get around this? Thanks

---

### Post by tonyr on 2006-07-05
I didn't go that route.  I installed the package from (repo entry)
> 
## for skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

and didn't have to do anything else.

---

### Post by dmizer on 2006-07-05
there's a skype beta for linux out now that supports alsa so you don't have to use the dsp hyjacker.  i've been using it for a while now in fedora core.  much nicer than the current pos.  better graphics, better interface, faster loading ... all around better design.  it is still beta, so there are still issues (for example bluetooth headsets have been reported as giving trouble.)

there's even a debian package:
[http://www.skype.com/download/skype/linux/13beta.html](http://www.skype.com/download/skype/linux/13beta.html)

---

### Post by mosestruong on 2006-07-05
OK - I've tried downloading the beta version, but I still get the same problem, just a different pointer...

*** glibc detected *** free(): invalid pointer: 0x08aa6758 ***
Aborted

---

### Post by aysiu on 2006-07-05
It looks to be *scim*-related:
[http://ubuntuforums.org/showthread.php?t=189126](http://ubuntuforums.org/showthread.php?t=189126)

---

### Post by dmizer on 2006-07-05
google shows this as a glibc error with malloc check:
> man malloc
...
       Recent versions of Linux libc (later than 5.4.23) and GNU  libc  (2.x)
       include a malloc implementation which is tunable via environment vari-
       ables.  When MALLOC_CHECK_ is set, a special (less  efficient)  imple-
       mentation  is  used  which  is  designed to be tolerant against simple
       errors, such as double calls of free()  with  the  same  argument,  or
       overruns  of a single byte (off-by-one bugs).  Not all such errors can
       be protected against, however, and memory leaks can result.   If  MAL-
       LOC_CHECK_  is  set  to  0,  any  detected heap corruption is silently
       ignored; if set to 1, a diagnostic is printed on stderr; if set to  2,
       abort() is called immediately.  This can be useful because otherwise a
       crash may happen much later, and the true cause  for  the  problem  is
       then very hard to track down.
are you using 64 bit dapper?

---

### Post by mosestruong on 2006-07-05
[QUOTE=aysiu]It looks to be *scim*-related:
[http://ubuntuforums.org/showthread.php?t=189126](http://ubuntuforums.org/showthread.php?t=189126)[/QUOTE]

Thanks - this was the problem indeed. I've created a script to launch skype without scim and it worked - but i wont be able to type chinese in it though - oh well at least everything else works.

---

### Post by tbraun on 2006-07-05
[QUOTE=dmizer]there's a skype beta for linux out now that supports alsa so you don't have to use the dsp hyjacker.  i've been using it for a while now in fedora core.  much nicer than the current pos.  better graphics, better interface, faster loading ... all around better design.  it is still beta, so there are still issues (for example bluetooth headsets have been reported as giving trouble.)

there's even a debian package:
[http://www.skype.com/download/skype/linux/13beta.html](http://www.skype.com/download/skype/linux/13beta.html)[/QUOTE]


Yes, I can confirm that this is a huge improvement. I cannot count the number of times I had to restart Skype, because it had a 'problem with sound device'. That was a terrible situation, but now, with 1.3 and ALSA support, that problem seems to be gone. Really, really nice. One endless source of daily annoyances less to deal with... :D 

Tom

---

### Post by tabun on 2006-07-07
First off, UBUNTU dapper rocks :-D 

](*,)  :-k Yes, I got this same error, after successfully installing the japanese keyboard on my dapper linux.  I installed dapper last week.

At least when I do the following, skype runs...ok, but with no scim enabled.
The odd thing is scim is running perfectly for every other application ooffice and thunderbird and firefox, except skype.

$ sudo bash
# export QT_IM_MODULE=
# skype &
# export QT_IM_MODULE=scim

Another skype annoyance I observed is when I am running other applications like xmms and mplayer, as soon as I change the volume skype seems to give me something about can't access sound device for the rest of the skype session and then I can call or receive calls from anyone else.

In the meantime, I can live with not having japanese input directly in skype through scim since I can go to ubuntu's text editor and type &#26085;&#26412;&#35486;&#12288;there and then paste it into skype :)  Also in the meantime, I can live with closing my mplayer and xmms when I know I am expecting a call through skype. :-?  I don't really want to have to do that since at times I noticed that once a call has been initiated, I can play xmms/mplayer and the caller can hear my music/video but when I adjust the volume anywhere :neutral:

And yes again let it be known UBUNTU dapper rocks :-D

---

