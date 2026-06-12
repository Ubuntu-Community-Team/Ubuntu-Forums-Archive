---
title: "Yet another DVD &quot;won't play&quot; thread"
date: 2005-12-23
forum: Desktop Environments
---

### Post by quietglow on 2005-12-23
My daughter just gave me an awsome DVD and I guess that means its time to get the DVD player working.

HP DV4000 laptop

New install of Breezy, I ran automatix adding all the extra codecs and also enabling DMA. When I play a video it gives me an "encoded DVD" error. I get some version of this error in Totem, VLC and Mplayer. Some DVDs will play the (presumably unencoded) titles, but never the DVD itself.

I've tried everything I can find on the forums, including other versions of the codecs.

Any other suggestions?

Thanks so much!

---

### Post by kingsidy on 2005-12-23
try do install the libdvdcss2 package manually. Look it up in the debian repositories or on the debian website. Install it. also install totem-xine by typing: apt-get install totem-xine . see what happens.

---

### Post by NeghVar on 2005-12-23
try the wiki:

[https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b](https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b)

it basically says the same thing.

---

### Post by quietglow on 2005-12-23
I've tried it before, but I'll take a look at those links here in a sec.

I'd forgotten about this, but it just occured to me as I'm seeing some errors dealing with region codes.

Don't DVD players generally have to be told which region they live in the first time they're run--like something that is saved in some sort of ROM? I remember having to do this when I got my last powerbook. This DV4000 machine never ran windows--I actually booted it up the first time with an Ubuntu install disk. Is that a problem? I was proud that windows never ran on it...

---

### Post by quietglow on 2005-12-23
okay, I should have read the Wiki first--I just found the region code setter. That doesn't look like it was the problem, though.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
Mplayer (don't know about the others) can pull region encoded data off the disc even when the player says no. It's a lot slower (ie cpu intensive) but you can do it. I have (for example) some korean dvds that used to trigger a prompt every time I played them. I just rip them to the hard drive using mplayer -dumpstream and watch'em from there. I cannot change the region encoding on my dvd drive any more (and it is region 1) but I have ripped these several times without complaint.

---

### Post by quietglow on 2005-12-23
After a reboot it works!! It looks as if it was the region code after all. I suppose that most DVD howtos assume the computer has run a DVD at some point previously--presumably in windows.

Thanks for the link to the wiki!

---

