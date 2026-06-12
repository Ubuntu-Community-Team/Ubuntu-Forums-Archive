---
title: "Gnome Panel network issue"
date: 2011-03-14
forum: Desktop Environments
---

### Post by camarojones on 2011-03-14
On most of my ubuntu installations, I usually keep a CPU and Network System monitor widget active.

On my current setup, reg ubuntu on an Ausu 1015pem, the network display only seems to be updating at a 1 sec rate.

I have provided a screenshot to show you what I'm talking about. My normal system monitor shows a smooth transition in my download rate, but the panel widget is on, off, on, off, etc. (My mouse pointer is pointing at the problem spot.)

Anyone know what can cause this?

I have changed the rate to 1000ms to keep the black bars from showing between the lines, but at the default it shows lines.

Thanks for any help ahead of time!
Tom

---

### Post by Krytarik on 2011-03-15
I took a look into this, tried it at my own system, even with a bigger download to see it more precise. And I don't have this behaviour.

- You have the update interval of the *real* System Monitor also set to 1 sec (default), right?
- It seems that you customized the colors of the network monitor, at least in Lucid those are yellow by default, not green. If so, please make sure, that only the background color is set to black.

---

