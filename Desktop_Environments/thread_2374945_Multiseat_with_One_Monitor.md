---
title: "Multiseat with One Monitor"
date: 2017-10-20
forum: Desktop Environments
---

### Post by rstone13 on 2017-10-20
I'm looking to set up a multiseat environment on my laptop where 2 users share the same monitor so that I can play some lan games as if they were splitscreen games. The only solution I've found that I'm certain would produce the results I'm looking for was posted in 2008 and therefore is horribly outdated. Most multiseat setups seem geared toward multiple monitors but I'd rather not have to buy and carry a 2nd monitor when I'm certain my 17" screen can handle what I'm trying to do.

I'll admit I'm a novice when it comes to linux but I'm willing to take the time to learn whatever prerequsite material that I need to learn in order to set this up properly. If anyone has a tutorial specifically geared toward one monitor that would be appreciated but I'm also happy with just a list of software that could help me accomplish this.

---

### Post by DuckHook on 2017-10-21
Welcome to the forums, rstone13.

I have no idea how to help you, because I don't see how your request can be achieved. To my knowledge, screen output can only be controlled by one X session. You want a single monitor to be controlled by two separate X sessions, and I don't think that's possible.

It *is* possible to run two windowed VMs within one session, but that means your game will be running in a VM, and moreover, using the primitive VM emulated graphic card. Very few people are happy running games in a VM, so that doesn't seem to be a realistic solution.

Perhaps it would help someone more knowledgeable than me if you post the link to this other solution that you've found.

---

### Post by rstone13 on 2017-10-21
Sure! Here's the solution [https://ubuntuforums.org/showthread.php?t=707796](https://ubuntuforums.org/showthread.php?t=707796). The way it seems presented, the 2nd x session is in a window that's launched from the 1st x session and is therefore on the same screen. Perhaps I'm misunderstanding it though.

---

### Post by DuckHook on 2017-10-21
That's a very clever solution that will probably still work today&#8212;at least in theory. I haven't seen that tutorial before. Thanks for bringing it to our attention.

The upshot is similar to the two VM solution. You are running one (or more) additional seats windowed. However, they would be using the native video driver on bare metal, so no VM penalty.

The details to this implementation are above my pay grade, but you might wish to play around in an experimental installation. You could install Ubuntu to a USB drive and tinker with that instance without compromising your main install. My habit is to dual boot into another install that I use only for the purpose of experimentation.

Good luck to your further explorations and let us know how it goes!

---

