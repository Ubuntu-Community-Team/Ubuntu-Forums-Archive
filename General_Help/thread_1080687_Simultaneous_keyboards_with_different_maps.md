---
title: "Simultaneous keyboards with different maps?"
date: 2009-02-25
forum: General Help
---

### Post by yther on 2009-02-25
OK, I know almost anything is possible, but I haven't been able to get my head around this one yet.  How would I go about having two different "keyboards" plugged in at once, both USB, with different software mapping for each one?

Here's the situation.  I use the Dvorak layout, remapped by software because Logitech doesn't make a Dvorak G15.  ;)  I also have a bar code reader that I'd like to use occasionally; the scanner is a USB device that's recognized as a HID keyboard.  If I'm reading numbers only, it's not a problem, but with letters and certain punctuation they all get messed up because they are remapped just like my real keyboard.  So for example, if I scan "PSU-12345-X" it comes out as "LOG[12345[Q"—not really useful.

Now, given that the real keyboard and the scanner have different device IDs, I'm wondering if one could somehow specify that the Dvorak layout should only apply to one of the devices and not the other.  Has anyone done something like this before, or know how it would be done?

Thanks for any clues!

---

### Post by geraldm on 2009-02-25
(Disclaimer: I have not tried this)
I would try to create a customized /etc/X11/xorg.conf OR the same file in the home directory, which may have to be a hidden filename ?

Create two different devices in the InputDevice section.
Use the Device line to assign each "keyboard" to its respective device.
One will have the dvorak layout.   There is a file in /etc/X11/xkb/symbols/dvorak
which might be the layout you use.  If I remember right, there were several minor variations to the dvorak layout, and you might have to customize a file. 

I probably would try something simple as a test first.  Maybe see if the xorg.conf file would work with two different existing layouts first.  If I succeeded there, then do the customization and editing after that.

Always backup any files you change, so you could revert if a mess is made.
I believe you would have to restart the X server to test the changes.  Three-finger salute  ctrl + alt + backspace should do it.

Good luck,
Gerald

---

