---
title: "setting up a Game Pad"
date: 2014-08-21
forum: Gaming &amp; Leisure
---

### Post by liferocket on 2014-08-21
I have a Razer Tartarus game pad that I use for Minecraft. It works out of the box, and most of the keys are configured to work exactly as the left side of a regular Keyboard. However, for optimal play I want to remap some of the keys to be the Esc key, and F11 and F3 and a few others. Previously, I was running 12.04 and found instructions on how to write a Keymap and put it in /lib/udev. However, this method is no longer available since I upgraded to 14 yesterday. All I can find through a google search are links to tools that no longer exist or are not updated to the current version. I found /lib/udev/hwdb.d/60-keyboard.hwdb, which seems to include keymaps specific to several individual Laptop keyboards, but nothing for my hardware and nothing that helps me figure out what I need to add. Any help or advice on what commands I can use to figure out the right Keycodes and how to edit the proper file would be much appreciated. I wish someone would write a nice GUI tool that lets you remap or turn off buttons for individual keyboards/joysticks and keep it up-to-date for the current version!

---

### Post by kostkon on 2014-08-21
Have you already tried [Antimicro]("https://github.com/Ryochan7/antimicro")?

---

### Post by vanity2 on 2014-08-22
> **liferocket said:**
> I have a Razer Tartarus game pad that I use for Minecraft. It works out of the box, and most of the keys are configured to work exactly as the left side of a regular Keyboard. However, for optimal play I want to remap some of the keys to be the Esc key, and F11 and F3 and a few others. Previously, I was running 12.04 and found instructions on [telecharger emulateur 3ds]("http://emulateur3ds-mac.blogspot.com") how to write a Keymap and put it in /lib/udev. However, this method is no longer available since I upgraded to 14 yesterday. All I can find through a google search are links to tools that no longer exist or are not updated to the current version. I found /lib/udev/hwdb.d/60-keyboard.hwdb, which seems to include keymaps specific to several individual Laptop keyboards, but nothing for my hardware and nothing that helps me figure out what I need to add. Any help or advice on what commands I can use to figure out the right Keycodes and how to edit the proper file would be much appreciated. I wish someone would write a nice GUI tool that lets you remap or turn off buttons for individual keyboards/joysticks and keep it up-to-date for the current version!

Maybe downgrading is the best option...

---

### Post by Ranko Kohime on 2014-09-04
xev will give you the keycodes, assuming the Tartarus shows up as a keyboard like I suppose it to.  I would logically assume you could just create a file in /lib/udev/hwdb.d or /etc/udev/hwdb.d, with a format similar to 60-keyboard.hwdb, but that is just an assumption.  My preference would be to avoid adding it into that particular file, as it will probably be overwritten the next time udev is updated.  Perhaps [this link]("https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes") will be of some value.

---

### Post by webercs1 on 2015-03-27
There is a software package called pystromo on sourceforge (I think), but it is manual set up through configuration files. It took me a while to feel ok with it, but once you set it up and make a script (optional but recommended) to activate it, it starts instantly. I prefer this.

For a GUI experience based on Java, try [http://sourceforge.net/projects/kbmaster/](http://sourceforge.net/projects/kbmaster/) .  It takes ten seconds or so to actually start, but works fine with a small learning curve. It reportedly works great with the n52te and later models.

I have an n50 & 52, and kbmaster was not written with those in mind. It had a few issues with my older hardware and I liked the challenge learning to use pystromo anyways, plus pystromo is instantly activated without the delay of opening a program first.

One of those should work great for you depending on your comfort level.

---

