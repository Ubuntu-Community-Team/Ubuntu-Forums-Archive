---
title: "Dead multi-media keys - xev does not respond"
date: 2006-01-25
forum: Desktop Environments
---

### Post by jsteve54302 on 2006-01-25
I have a MS Digital Media Pro keyboard (currently on a USB port, could move to PS/2 if that would help), and many of the multimedia keys are well and truly dead - as in stake-through-the-heart, cannot be resurected, don't even seem to send scan codes at all dead.  xev does not respond at all when they are pressed, and using the <ctrl>-<alt>-F1 trick doesn't help with any of my multimedia keys.  Is there anything I can do to bring these keys back to life, other than writing a new kernel module (I'm not nearly that good)?  Or should I start making little headstones for them now?  I'm assuming the keys must be sending scancodes to the kernel (they work under Windows, and the other multimedia keys at least are recognised by xev), so how do I get the kernel to send them on without any idea what scancodes the kernel is getting?

These are the keys that do not respond (clockwise from left of kb):

1. "Zoom slider" - like an auto-centering joystick throttle
2. Programable Shortcut Keys number "1" - "5", and My Favorites used tor program shortcut keys under windows
3. My Documents
4. My Pictures
5. My Music
6. Messenger
7. Lock Screen

Those of you familiar with this keyboard probably noticed that I skipped 11 keys - these do show up in xev, and I plan to use .xmodmap to get these to function (I'm using XFCE, and can't seem to find the Gnome keyboard shortcut app).  I just don't want to do anything, and find out to get the other keys working will change how the are mapped.

TIA,
John

---

### Post by BitTorrentBuddha on 2006-05-11
I have the exact same problems with the dead keys bit, but for the multimedia keys that do show up in xev, you could probably put them into xbindkeys ```
# apt-get install xbindkeys xbindkeys-config
``` and then start xbindkeys first followed by xbindkeys-config, just plug the state and keycode in under the "Key :" field as m:<state> + c:<keycode>
but if anyone can figure out the dead keys bit, I would be very grateful.

---

