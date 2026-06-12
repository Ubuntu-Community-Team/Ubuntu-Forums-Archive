---
title: "Make firefox load faster?"
date: 2009-04-25
forum: General Help
---

### Post by josephellengar on 2009-04-25
I know that this question has been asked before, but I couldn't find any how-tos for anything past feisty.  Thanks!  I could really use the help.

---

### Post by sports fan Matt on 2009-04-25
Even though it says this is for FF 2..Ive applied the tweaks here for 3.0..Any difference? [http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/](http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/)

---

### Post by josephellengar on 2009-04-25
> **sox fan Matt said:**
> Even though it says this is for FF 2..Ive applied the tweaks here for 3.0..Any difference? [http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/](http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/)

Thanks, but I don't mean surfing speed.  I mean loading the program itself.

---

### Post by murderslastcrow on 2009-04-25
Well, there is a Firefox spinoff made specifically for Linux called "Swift-Fox." It shares the exact same files, just has some different configuration that some users say improve performance quite a bit.

It'd be interesting to know what the specs on your system are, such as RAM and Video Card, since this may be an issue related more closely to graphics speed than actual program speed. What kind of delays are you experiencing? Or are you just trying to optimize the experience to the furthest?

---

### Post by josephellengar on 2009-04-25
> **murderslastcrow said:**
> Well, there is a Firefox spinoff made specifically for Linux called "Swift-Fox." It shares the exact same files, just has some different configuration that some users say improve performance quite a bit.

It'd be interesting to know what the specs on your system are, such as RAM and Video Card, since this may be an issue related more closely to graphics speed than actual program speed. What kind of delays are you experiencing? Or are you just trying to optimize the experience to the furthest?

It's an older system.  128 mb nvidia graphics card, dual core 800mhz processor, 1 gb of RAM.  The program just loads very slowly on startup.  I get maybe a 10 second or so wait.  I think that some of it might be because I am a little addon-crazy.

---

### Post by codeseer on 2009-04-25
I second the request for hardware information.

Swiftfox is a third party distribution of Firefox where they have taken the source code and built it with optimizations for either AMD or Intel processors, depending on which one you download. You would see a slight improvement in speed by using Swiftfox; I don't think it's going to be a show stopper though.

The loading and closing times of Firefox are greatly affected by both the amount and types of addons you have installed to it. I might suggest using separate profiles for your needs; having one that has no addons and one with the addons you need for specific tasks. This can be accomplished by running the following command:

```
firefox -profilemanager -no-remote
```

...This command can also be placed in a short cut for fast access and it will allow you to run instances of separate profiles at the same time if you wish.

---

### Post by Monotoko on 2009-04-25
> **idigchess said:**
> It's an older system.  128 mb nvidia graphics card, dual core 800mhz processor, 1 gb of RAM.  The program just loads very slowly on startup.  I get maybe a 10 second or so wait.  I think that some of it might be because I am a little addon-crazy.

Addons definatly will slow down firefox, try to start it without any and see if that improves your speed.

---

### Post by codeseer on 2009-04-25
> **idigchess said:**
> It's an older system.  128 mb nvidia graphics card, dual core 800mhz processor, 1 gb of RAM.  The program just loads very slowly on startup.  I get maybe a 10 second or so wait.  I think that some of it might be because I am a little addon-crazy.

I'd say 10 seconds is good for that hardware, seeing that you like addons as well.

Edit:

You might also give 'preload' a try; it can be gotten from the repositories with Synaptic. If I were you, I'd [get it from here]("http://sourceforge.net/projects/preload") though, because it's a much higher version number.

In this particular test, Firefox went from ~11 seconds to ~5 seconds on load time by using it.

[http://www.kabatology.com/02/27/drastically-reduce-the-ubuntu-launch-time-with-preload/]("http://www.kabatology.com/02/27/drastically-reduce-the-ubuntu-launch-time-with-preload/")

However, I'm not sure how it will behave with only 1 GB of RAM.

---

### Post by josephellengar on 2009-04-26
> **codeseer said:**
> I'd say 10 seconds is good for that hardware, seeing that you like addons as well.

Edit:

You might also give 'preload' a try; it can be gotten from the repositories with Synaptic. If I were you, I'd [get it from here]("http://sourceforge.net/projects/preload") though, because it's a much higher version number.

In this particular test, Firefox went from ~11 seconds to ~5 seconds on load time by using it.

[http://www.kabatology.com/02/27/drastically-reduce-the-ubuntu-launch-time-with-preload/]("http://www.kabatology.com/02/27/drastically-reduce-the-ubuntu-launch-time-with-preload/")

However, I'm not sure how it will behave with only 1 GB of RAM.

Holy crap, thank you so much.  That worked *really* well.  I'm down to only six seconds.  And running it without the addons brings it down to only three.

---

### Post by TheLions on 2009-04-26
check my sig!

---

