---
title: "Startup blank screen"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by sghayal on 2007-12-06
I am using using Ubuntu 7.x and finding this very annoying issue. What I see that during startup after seeing the line for time sync my screen goes blank for like 2-4 minutes and then it returns back with the GUI.

My understanding is that during this time Ubuntu is starting up and doing some initialization stuff but it would be nice if I could see something on the screen instead of blank screen. First time it happened I thought Ubuntu was not starting up and so I ended up doing reinstall. And then Second time I simply thought of waiting it out and wallah it started up.

I am not sure what is causing this issue and wondering if we can improve this so that we can see some lines of initialization (like in other linux/unix systems) or may be a steady screen with moving task bar (like windows) would be very useful.

I had noticed similar issue with ubuntu 6.x too but in that case the wait window was very small (may be because 6.x was running on better machine then what I am using for 7.x).

Thanks for your time.

Cheers,

Sandip Ghayal

---

### Post by alarme on 2007-12-06
edit /boot/grub/menu.lst
delete splash and quiet options
also, at the end of the same line, you can try to add vga=791, to see 1024x768 console framebuffer (be careful, some adapters / distros don't work well with this)

---

