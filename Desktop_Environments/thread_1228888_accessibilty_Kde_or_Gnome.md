---
title: "accessibilty Kde or Gnome?"
date: 2009-08-01
forum: Desktop Environments
---

### Post by bailbath on 2009-08-01
My daughter was physical disabilities and finds it hard to use a mouse she uses a trackball but in Gnome the mouse still is too fast for her even after using the gnome accessibility utility. Is Kde any better or is there another way to slow the mouse?
Thanks
Ian

---

### Post by wojox on 2009-08-01
What about System > Preferences > Mouse
Did you adjust it there?

---

### Post by bailbath on 2009-08-02
Yes it is still too fast! She has used windows upto now and that was ok because mouse speed could be slowed right down. There must be a way to slow it further?
Ian

---

### Post by Dullstar on 2009-08-02
Did you slow it down ALL THE WAY?

---

### Post by bailbath on 2009-08-03
Yes of course!

---

### Post by ugm6hr on 2009-08-03
I have never edited xorg settings for the "mouse" driver, which I assume trackballs use.

However, it should be the same as any other xorg edit.  Remember, Intrepid + Jaunty require fdi edits rather than a direct xorg.conf edit.

Links: [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL)

Looks like the mouse driver has a "Sensitivity" setting (Ref: [http://blog.khax.net/2009/02/08/adjusting-mouse-and-touchpad-speed-in-xorgconf/](http://blog.khax.net/2009/02/08/adjusting-mouse-and-touchpad-speed-in-xorgconf/) )

It also has a "Resolution" setting, apparently (Ref: [http://www.linuxquestions.org/questions/slackware-14/how-to-set-mouse-sensitivity-in-xorg.conf-not-window-manager-425552/](http://www.linuxquestions.org/questions/slackware-14/how-to-set-mouse-sensitivity-in-xorg.conf-not-window-manager-425552/) )

The Sensitivity setting is not mentioned here though: [http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html) .  Can't find any documentation for newer X11 online - must exist somewhere though.

Using the Logitech Mouse as an example (assuming it is correct), and setting arbitrary Sensitivity & Resolution:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">mouse</merge>
   <merge key="input.x11_options.Sensitivity" type="string">**0.3**</merge>
   <merge key="input.x11_options.Resolution" type="string">**260**</merge>
  </match>
 </device>
</deviceinfo>
```

Something like that should do it.... Try experimenting with the **0.3** and **260** values.

This will affect any mouse plugged in... Presumably you could edit it as per the Logitech example to affect only that specific Trackball (using product ID etc).

Another reference: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

Good luck...

---

### Post by bailbath on 2009-08-05
Thanks I will give that a try. It's a shame that the slider in the mouse gui doesn't slow it right down! I will report back if this works:D
Ian

---

