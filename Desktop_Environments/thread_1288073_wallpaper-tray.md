---
title: "wallpaper-tray"
date: 2009-10-10
forum: Desktop Environments
---

### Post by noname580 on 2009-10-10
So i wanted to try out the wallpaper-tray applet instead of drapes.  so i add it from synaptic and add it to my top panel.  i change some settings so it will randomly change.  me being a slight idiot i didnt change the timing from one.  So i clicked okay and it started changing wallpapers wicked quick.  Due to that i couldnt right click and go into preferences.  So i went to system monitor and killed the process.  When i tried to re add the applet there is no longer an icon on my top panel.  I went back into synaptic and completely removed it.  I even restarted my computer and still when i add it to my panel there is no icon and it changes wallpaper every second.  Anyone know how i can get the icon to come back so i can try and change the preferences or at least give me a reason on why it happened.  Thanks for your time.

---

### Post by mac9416 on 2009-10-10
I've had the same problem. So irritating. Here's how I fixed it.

Kill the wp-tray process then run...

```
$ gconf-editor
```

There is a setting under /apps/wp_tray/. I forget what it's called, but it controls the time between wallpaper changes. You need to set it to 1 or more. Then reboot and it should be OK.

wp-tray is rather janky, but it gets the job done. I wish there was a better option, seeing as Win7 has nice wallpaper slideshows.

Good luck!

---

### Post by noname580 on 2009-10-10
Oh thank you.  it was driving me insane

---

### Post by Ubunthree on 2009-10-23
Is there a way to stop wallpaper-tray from using the stock Ubuntu backgrounds? I have it set to look in a single directory of my own images, which it does fine, but it also keeps throwing in the stock backgrounds, and I can't seem to convince it that I don't want it to.

---

