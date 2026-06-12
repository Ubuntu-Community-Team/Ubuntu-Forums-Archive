---
title: "Inspiron 9300 external monitor in gutsy (w/picture)"
date: 2007-11-12
forum: Dell  Ubuntu Support
---

### Post by deruberhanyok on 2007-11-12
Hey guys. Lengthy post ahead. Picture included.

I found a few outdated posts that didn't quite apply to this particular problem so I'm making a new one. Here's the situation:

I have an Inspiron 9300 laptop. For various reasons I can't easily connect it to the internet, so I'm limited to what is available with the default Gutsy install. This particular system has a 2GHz Pentium M, 1GB of RAM and onboard Mobility Radeon X300 graphics with 32MB of memory. It's using the default open-source 'ati' driver.

I ran into an odd problem when I tried to connect an external monitor. The screen on this inspiron has a native resolution of 1440x900 and the external monitor is an HP 2335 with a native res of 1920x1200, connected via DVI.

When I close the laptop lid both screens blank for a while, then the external monitor comes up looking like the picture I've attached (it's been scaled to 50% size). You can see that it seems to recognize that the whole 1920x1200 resolution is available but the top and bottom gnome panels extend 1440 pixels across the screen and the bottom panel stops at 900 pixels, basically framing out the laptop screen's native res.

Further, it doesn't recognize that the laptop lid is closed and I can see the light coming from the display when I close it.

The 'screens and graphics' control panel doesn't recognize that there is a second monitor attached, and if I force enable one the application crashes without changing anything. Specifying the monitor type as an HP L2335 doesn't change the display, nor does calling it a plug and play monitor or a "widescreen LCD panel 1920x1200".

Even stranger, if you'll check the picture I posted, see how some of the gnome file browser windows extend past the boundries of the gnome panels? The gnome panels seem to be stuck on the 1440x900 resolution of the laptop screen. The laptop screen shows those file browser windows being cut off, so it recognizes that there is more desktop space than the laptop screen's native res.

The xorg.conf file is unchanged from the install. I don't have the contents of it handy but I can post it later if needed... I had hoped that the output hotplugging would make manual editing of that file unnecessary.

So:

1) What can I do to get it to realize I've closed the lid and only want to use the external monitor?

2) How can I get the proper display out of the external monitor?

3) How can I get it set up to use two displays as an extended desktop instead of this weird cloning that is currently happening?

If I had to guess I'd say it's a result of something that isn't yet supported in the 'ati' X driver, but I don't have a way to update anything on the system right now.

Thanks in advance,

---

### Post by deruberhanyok on 2007-11-14
Turns out Fedora 8 has the same problems. Any thoughts?

---

### Post by deruberhanyok on 2007-11-16
I guess this question would be better placed in another forum... hardware& laptops maybe? Is it possible to move it or should I just repost it there?

---

