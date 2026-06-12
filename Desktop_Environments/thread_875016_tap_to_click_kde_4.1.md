---
title: "tap to click kde 4.1?"
date: 2008-07-30
forum: Desktop Environments
---

### Post by chrisby on 2008-07-30
Does anyone know how to disable tap to click on kubuntu kde 4.1, or is that not a feature yet?

---

### Post by benerivo on 2008-07-30
I don't think it's a feature yet, but you should still be able to do it by adding a line to your /etc/X11/xorg.conf file as described [here.]("http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/")

One of the commands in this link, uses gedit to edit the xorg.conf file. As you won't have this in kde, you could use the terminal text editor nano instead.

---

### Post by Lewisu on 2008-11-10
It's 1:14am and I've finally fixed this problem.

In Ubuntu 8.10 the xorg.conf file seems to be very generic. At least for me, adding the "Input" options in this file bore no fruit.

So, you have to create the file "/etc/hal/fdi/policy/11-synaptics-options.fdi"

Write the following lines into this new file:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="synaptics">
    <merge key="input.x11_options.SHMConfig" type="string">On</merge>
    <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
  </match>
</device>
</deviceinfo>


that will disable tapping.

Hope this helps. Good night!
Lew.

---

### Post by nuclearlee on 2009-01-11
Thanks!!! I was about to scream.  I really can't stand tap to click.

> **Lewisu said:**
> It's 1:14am and I've finally fixed this problem.
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="synaptics">
    <merge key="input.x11_options.SHMConfig" type="string">On</merge>
    <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
  </match>
</device>
</deviceinfo>


---

### Post by carnagex420x on 2010-03-03
THANX! Tap to click in Backtrack 4 was driving me insane.

- Works in BT4 BTW too.

---

