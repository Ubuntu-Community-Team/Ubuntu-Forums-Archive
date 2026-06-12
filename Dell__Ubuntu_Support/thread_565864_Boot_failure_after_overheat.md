---
title: "Boot failure after overheat"
date: 2007-10-02
forum: Dell  Ubuntu Support
---

### Post by louca on 2007-10-02
Ok, here is what happened..

Finally got ubuntu on to my vostro 1400 and it was working great except for the sound.

Ran automatix to install alot of stuff, did an update, then restarted. During the shutdown, i got two messages telling me that the cpu cores had soft locked.

When i turned it off and then back on, a message came up telling me that the laptop was approaching dangerously high temperatures probably due to fan inoperation. So I turned it off and left it for a while.

When it was completely cool I turned it back on, this was about 4 hours later.
It took a really long time to load the bios, then it went to grub and I started linux.

It started ordinarily enough, but then suddenly it just stopped. The screen went blank. No nothing!

I turned it off then back on again, this time the bios loaded in normal time and I tried again, same thing happened. I pressed alt +f1 to see what was going on and there was nothing.. the words just disappeared!

Suggestions? Vista is loading normally and operating normally so I am thinking it may be automatix which caused this.

---

### Post by louca on 2007-10-02
Ok..

I started in recovery mode and typed in automatix-nvidia-restore

It worked.. guess I will be installing those drivers the hard way.

---

### Post by saru411 on 2007-10-03
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

envy will install the nvidia drivers for you. its very simple to do. after you get the driver installed type this into terminal.

> sudo nvidia-settings

now set up your screen resolution and save the xorg file. restart x with contrl + alt + backspace.
 

hope this helps =)

---

