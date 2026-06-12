---
title: "Xine: DVD playback in fullscreen mode jerky suddenly"
date: 2006-05-21
forum: Desktop Environments
---

### Post by timetunnel on 2006-05-21
Hi,
I've been very satisfied with DVD playback on my IBM R52 laptop using xine-ui since Breezy came out. However, suddenly it goes jerky when in fullscreen mode. After a while I get a message saying "too much dropped frames...". Going back to non-fullscreen mode plays fine. Playing video files from harddisc (avi, mpeg etc.) is not as jerky as DVD but has definetely gotten worse as well. 
I could still watch a DVD without any problems two days ago and since then I have changed absolutely *nothing* in my setup. Soooo, any idea where to start looking?

Thanks
Jens

---

### Post by Ramses de Norre on 2006-05-21
Did you apply the xorg updates recently? They came out a week ago I think and they might have broken some features of your graphics driver. To solve it just reinstall the driver.

---

### Post by timetunnel on 2006-05-21
Yes, I did that, but on  May 4th, and I have watched several DVDs since then without problems. The problem I described must have developed over the last two days.

---

### Post by Lord Illidan on 2006-05-21
Make sure that dma is turned on.

And run top in a terminal, to see if a process is hanging up your cpu.

---

