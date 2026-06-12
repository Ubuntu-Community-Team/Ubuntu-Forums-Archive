---
title: "Return of the M2010"
date: 2009-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SterLo on 2009-01-06
So I've decided to take on the challenge of getting my Dell XPS M2010 to work 100% with Ubuntu.

I know that may be impossible. But DAMMIT I thought I would try!

So far I have X configured to my liking, my keyboard works (I am on the M2010 as I write this), my USB ports all work and my wireless works.

I have installed Ubuntu 8.10.

Here are the problems so far:

1) Sound only works from my sound jack for the headphones. Which means I can only heard things when I plug in my headphone. So that sucks the most right now.

I have gotten pretty good at messing with sound on several machines. I've read another article or two and it looks like this is a common problem with this machine and Ubuntu and no one has solved it yet.

2) My bluetooth keyboard works...but my mouse doesn't.
I am trying to get it to add my mouse...I put the mouse into search mode and I tell it to scan...no luck. So I was hoping someone could give me some pointers.

I ran hcitool scan and got:
Device is not available: No such device

I was reading the following to try and solve it, but ran into the above issue: [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

3) The keyboard works but the lights don't work. So right now the numlock light is on all the time but none of the other lights come on. Now the keys do work, SO IF I TURN ON CAPSLOCK it does work, but the light doesn't do anything.

4) Was wondering if anyone has any clever ideas on how I can get the remote for the media center to work on the machine. I thinnk installing Wine and then seeing if I could get the Media Center software installed through that and then having the computer recognize the remote...I could be on the right path. But I was wondering if anyone else would have experience in that.

I think that's it for now.

I appreciate help anyone offers!

---

### Post by SterLo on 2009-01-07
/Bump
/10car

Grep Advice *

---

### Post by Kid-k on 2009-01-25
I think what you are doing is great , I had lots of problems with my m2010 and ubuntu on Gutsy and ended up ditching for windows ( I'm a newb to linux and only had it for a few days in hopes I could return back to it once people solved some problems)

Here's my take:

(1) Sound is the main issue everyone has but I haven't seen anyway try the 5.1/7.1/spdif outputs on the m2010 while using linux , please try these...right now my lappy is hooked up to a 5.1 system and I'm sure I could deal with the lack of sound out of the internal speakers if the 5.1 worked

(2)I know I managed to get my mouse and keyboard to both work when I had ubunutu installed , i forget how I got the mouse to work although i remember having some trouble, something i do remember as well is having to use the Bluetooth pin that is printed on the bottom of the mouse. I also did reinstall the dell bluetooth drivers at some point while trying to get this to work but I'm not sure if this did anything significant. A problem I did have with my bluetooth though was getting it to work in the longhorn bootloader(I was trying to run a bualboot) or the bios during a cold boot or restart out of linux, the only way it would work at startup is if I restarted from vista, I did not try this with grub,. Can you please test this and see what you find?

(3)don't really know much about this one but something I have noticed while running vista is sometimes the caps lock or num lock will be on and the light won't be......if i turns caps/num lock off and then back on then the light will come on....this mainly happens at startup... do you find that your media keys work ?


(4)I know that the remote is not a bluetooth device like the mouse or keyboard but instead works by RF, maybe there are RF drivers out there or something ?


Hope some of this helps you.....I am planning on trying ubuntu again shortly and committing myself to trying to get it work but first I'm going to buy a cheap machine that is proven to work with linux so that during the time when this one is having trouble and I am trying to csolve problems , I can work from the other machine

---

### Post by SterLo on 2009-01-26
Hey Kid-K,

Thanks for the response!
I was defeated by the issues I was having...
I ended up going back to Windows :-(

Sound would be AWESOME...that's what I missed most.

I also really wish I could get the mouse working...if you could remember what you did to make that work - that would be a step forward.

I think there's tutorials for getting the remote to work - so I wasn't too worried about that. It's the other two things that had me stalled.

The lights on the keyboard are controlled by software.
I think it's called QuickSet.
So maybe if that software was installed they would function properly.

Once again - thanks for the response!

> **Kid-k said:**
> I think what you are doing is great , I had lots of problems with my m2010 and ubuntu on Gutsy and ended up ditching for windows ( I'm a newb to linux and only had it for a few days in hopes I could return back to it once people solved some problems)

Here's my take:

(1) Sound is the main issue everyone has but I haven't seen anyway try the 5.1/7.1/spdif outputs on the m2010 while using linux , please try these...right now my lappy is hooked up to a 5.1 system and I'm sure I could deal with the lack of sound out of the internal speakers if the 5.1 worked

(2)I know I managed to get my mouse and keyboard to both work when I had ubunutu installed , i forget how I got the mouse to work although i remember having some trouble, something i do remember as well is having to use the Bluetooth pin that is printed on the bottom of the mouse. I also did reinstall the dell bluetooth drivers at some point while trying to get this to work but I'm not sure if this did anything significant. A problem I did have with my bluetooth though was getting it to work in the longhorn bootloader(I was trying to run a bualboot) or the bios during a cold boot or restart out of linux, the only way it would work at startup is if I restarted from vista, I did not try this with grub,. Can you please test this and see what you find?

(3)don't really know much about this one but something I have noticed while running vista is sometimes the caps lock or num lock will be on and the light won't be......if i turns caps/num lock off and then back on then the light will come on....this mainly happens at startup... do you find that your media keys work ?


(4)I know that the remote is not a bluetooth device like the mouse or keyboard but instead works by RF, maybe there are RF drivers out there or something ?


Hope some of this helps you.....I am planning on trying ubuntu again shortly and committing myself to trying to get it work but first I'm going to buy a cheap machine that is proven to work with linux so that during the time when this one is having trouble and I am trying to csolve problems , I can work from the other machine

---

