---
title: "OSS Problem"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Dark Shikari on 2006-07-13
When I first installed Ubuntu, OSS sound worked fine.  I installed and started Cedega, for example, and the OSS sound test worked and it played the sound.  The Ur-Quan-Masters worked, and had sound.  Starcraft worked with Cedega, and had sound.

Now, in the past few days, something happened to break that.

None of the aforementioned applications have sound.  The OSS test "succeeds" in Cedega with a green light, but the sound doesn't play.

However, the Ubuntu sounds work fine, and all media players work, because those use ALSA, which works fine.

What probably makes it harder is that my computer has both integrated sound and a Santa Cruz (Crystal Soundfusion 64xx).  This means that at least in Ubuntu I have to change the sound to the Santa Cruz in the settings to make sound work.  This could be a source of the problem: in which case I would ask how I would disable my integrated sound, which doesn't work properly with OSS anyways, it seems.

---

### Post by Dark Shikari on 2006-07-13
bump?

---

### Post by Dark Shikari on 2006-07-13
any ideas?  my post keeps going off the front page ](*,)

---

### Post by Dark Shikari on 2006-07-13
bump?

---

### Post by Dark Shikari on 2006-07-13
Any help?  :-|

---

### Post by Dark Shikari on 2006-07-14
Anyone? ](*,)

---

### Post by Dark Shikari on 2006-07-14
>_> <_< :eek:

---

### Post by Dark Shikari on 2006-07-14
...........

---

### Post by Dark Shikari on 2006-07-14
bumpity bump bump...

---

### Post by Dark Shikari on 2006-07-14
nobody knows... bah...

---

### Post by Dark Shikari on 2006-07-15
How can nobody know the answer to this ](*,)

---

### Post by bulldog on 2006-07-15
The integrated soundcard you can disable in the BIOS as far as I know.
The reason why your soundcard stopped working I have no clue.
Try to set it up by reinstalling your soundprogram.
With a little luck you get it working again.

edit:typo's

---

### Post by Kadin2048 on 2006-07-15
I have no idea why it would spontaneously stop working like that, but if you're using Dapper, I question why you're using OSS at all and not ALSA.

I've used ALSA and Cedega, and it works just fine. (Granted I haven't used it in a while, but it worked fine last time I tried it, and other sound stuff works fine.)

You might find these links helpful.

[http://www.linuxhardware.org/article.pl?sid=01/03/06/179255&mode=thread]("http://www.linuxhardware.org/article.pl?sid=01/03/06/179255&mode=thread") 
Note this article is from 2001 and as such, some of its conclusions are out of date; ALSA is in my mind now the clear choice over OSS, unless you have a card that's only supported in OSS. 

[http://ubuntuforums.org/showthread.php?t=161817&highlight=alsa]("http://ubuntuforums.org/showthread.php?t=161817&highlight=alsa")
This focuses on SB Live cards but it's not a bad intro to ALSA.

[http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/")
Lists of supported and supportable cards for ALSA.

I think in Cedega there is an option whether to use OSS or ALSA sound, and two different tests -- one which tests OSS and another which tests ALSA. I would check to see if ALSA is working, and switch Cedega to that. If it's not working, then you have a problem to fix and you can start working on that ... I think you'll find that you'll get a lot more help with ALSA problems than with OSS problems, since most people today use ALSA (or at least that's been my experience).

Oh, and the obvious first check to see if ALSA is working is to reboot and watch the bootup messages (or look at syslog) and see if ALSA starts up on boot successfully. At least on my system, it "just works" with the built-in sound. You might need to do some configuring, or disable the internal sound, in order for ALSA to "see" the other card ... but it should be capable of using them both, I would think.

So anyway, I'd switch to ALSA and then see if that works automagically, and if it doesn't, then I'd start asking for help with ALSA, rather than messing with OSS. (Provided of course your card isn't one of the few that's only supported under OSS.)

---

