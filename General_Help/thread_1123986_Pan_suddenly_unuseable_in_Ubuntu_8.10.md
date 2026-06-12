---
title: "Pan suddenly unuseable in Ubuntu 8.10"
date: 2009-04-12
forum: General Help
---

### Post by futz on 2009-04-12
I've run Pan newsreader for many years now. It's no Agent/Newsleecher, but I like it. I had been running Ubuntu 8.04 until a few weeks ago, and decided to finally scratch it and install 8.10. Very soon after that I noticed problems with Pan. It may have been after an update, but I don't remember exactly when it started.

When downloading headers, Pan downloads for a little while and then stops downloading, cranks one core to 100% and does something for a while. Then it downloads a bit more, stops downloading and does the one-core-to-100% thing again. It does this over and over, each time getting longer and longer as there are more headers for it to do whatever it's doing in the 100% processing stage.

WEIRD!!! This is totally new behavior for Pan. I've never seen it do this till I moved to Ubuntu 8.10. Pan has become unuseable. Takes hours or days to get headers.

I was running Pan v0.132 when the problem first appeared. I compiled v0.133 and nothing changed. Same problems.

I renamed the .pan2 directory and re-entered all my info and tried again. No change.

The computer is a quad-core 3.0GHz and has 4 gigs of RAM. I'm not running out of RAM, according to System Monitor. I used to run 2 gigs of RAM and Pan DID routinely run out of RAM on large groups. Giving it more RAM helped immensely. But all that was before the strange problem described above reared its ugly head.

---

### Post by futz on 2009-04-13
**Yeah! Cured it totally!** Runs wicked fast now. I dug around a bit in the pan-users mailing list archive and it turns out that I had Assistive Technologies enabled on my computer somehow. I have no idea how I managed that. I sure don't remember enabling it.

The cure is to go to **System/Preferences/Assistive Technologies** and uncheck **Enable assistive technologies**. Reboot just to be sure and restart Pan to test it.

---

