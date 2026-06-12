---
title: "Slow Flash?"
date: 2009-04-18
forum: General Help
---

### Post by kooldino on 2009-04-18
I run Firefox on Kubuntu 8.04 using the flashplugin-nonfree package for my flash support.  It works, but I've never been happy with it's performance.  I have a reasonably fast machine, yet if I try to view a youtube video in full screen, it's a slide show.

Should I be running a different flash plugin?  If so, which?  Are there any tricks I need to know to get things running right?

Any help would be appreciated.

---

### Post by justin_guerin on 2009-04-18
You may have a fast computer, but even so, some built in graphics chips aren't powerful enough to view flash in full screen.  I have a Dell Latitude D610 with an Intel Mobile 915GM, and full screen is a bit of a slide show on it. :(

To optimize, I'd recommend shutting down applications that are utilizing the CPU (use top to find out if there are any resource hogging programs currently running), make sure your video card is properly configured, and if all else fails, reduce your resolution to something like 1024 x 768, then watch full screen.  

Oh, and be aware that your performance will be worse just after startup, due to many daemons that may be running / starting up.  My flash performance gets noticeably better once my system has been up a bit.

---

### Post by kooldino on 2009-04-20
> **justin_guerin said:**
> You may have a fast computer, but even so, some built in graphics chips aren't powerful enough to view flash in full screen.

I built the PC myself, the graphics aren't on-board.  I can't remember the exact model of the card, but it's a newer entry-level nvidia card.

> To optimize, I'd recommend shutting down applications that are utilizing the CPU (use top to find out if there are any resource hogging programs currently running), make sure your video card is properly configured, and if all else fails, reduce your resolution to something like 1024 x 768, then watch full screen.

I'm running nvidia drivers, and all else works as it should.  Standard mpegs and such run in full screen without a hitch.

> Oh, and be aware that your performance will be worse just after startup, due to many daemons that may be running / starting up.  My flash performance gets noticeably better once my system has been up a bit.

I haven't noticed that, but:

dino@nebula:~$ uptime
 02:03:23 up 9 days,  2:04,  1 user,  load average: 1.57, 1.73, 1.73

---

### Post by Yellow Pasque on 2009-04-20
[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

---

### Post by Vaphell on 2009-04-20
do you have flash9 or 10 installed?

---

### Post by sandy8925 on 2009-04-20
Yeah I have the same problem too! Flash is just too sluggish. The situation sort of improved after using the new graphics card drivers but it's still not good enough. The funny thing is that Flash is faster on Firefox than on Opera. Right now I'm using Swiftfox and it's faster than both.

---

### Post by kooldino on 2009-04-20
> **Temüjin said:**
> [http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Very interesting.  Wonder if Youtube qualifies for this:

> Starting in the most recent Astro Beta, Flash Player supports new GPU acceleration modes. This acceleration doesn't automatically speed up legacy content. Instead, new SWF content has to be authored specifically to take advantage of this.

---

### Post by kooldino on 2009-04-20
> **Vaphell said:**
> do you have flash9 or 10 installed?

How can I tell?

---

### Post by kooldino on 2009-04-23
bump

---

### Post by kooldino on 2009-04-24
Ok, so I wasn't sure which version I had, and even though I was reluctant, I went ahead and uninstalled flash-plugin-nonfree and installed adobe flash 10.  


After I reinstalled, my sound wouldn't work, but after a reboot, everything works nicely,  Youtube videos are smooth, and I can view them in full screen happily!  Thanks, all.

---

### Post by kooldino on 2009-04-27
All is not well in Oz...I occasionally get no sound from youtube videos that should have it.  :(

---

