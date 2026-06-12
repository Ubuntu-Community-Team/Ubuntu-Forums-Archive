---
title: "Karmic: Xorg + HAL, input device properties won't work"
date: 2009-11-19
forum: Desktop Environments
---

### Post by colo on 2009-11-19
Hello forums,

I'm trying to enforce system-wide X-server keyboard rules via HAL. The 
procedure works perfectly fine on Gentoo GNU/Linux with comparable software 
(read: similar versions of hald and xorg-server), but I cannot get it to work 
on Ubuntu Karmic.

I edited /etc/hal/fdi/policy/preferences.fdi to read like the following 
(comments omitted):

----snip----
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
   <match key="info.capabilities" contains="input.keyboard">
      <merge key="input.xkb.model" type="string">evdev</merge>
      <merge key="input.xkb.rules" type="string">xorg</merge>
      <merge key="input.xkb.layout" type="string">de</merge>
      <merge key="input.xkb.variant" type="string">nodeadkeys</merge>
      <merge key="input.xkb.options" type="string">compose:caps</merge>
   </match>
</device>
</deviceinfo>
----snip----


HAL is absolutely silent when being restarted, unless I garble the XML on 
purpose - only then, error messages appear in the logs. Therefore, I assume my 
file is well-formed and parses correctly.

My keyboard settings, however, don't change at all. Querying the keyboard via 
HAL with the above configuration in place and loaded/interpreted yields the 
following:

----snip----
  input.xkb.options = 'lv3:ralt_switch'  (string)
  [...]
  input.xkb.rules = 'xorg'  (string)
  input.xkb.model = 'pc105'  (string)
  input.x11_driver = 'evdev'  (string)
  [...]
  input.xkb.layout = 'de'  (string)
----snip----


Please note that the device in question should match on "info.capabilities", 
"input.keyboard":

----snip----
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 
'input.keys', 'button' } (string list)
----snip----


What the hell is going on here?

Thanks in advance for hints and replies!

(Please note that I also [posted]("https://lists.ubuntu.com/archives/ubuntu-users/2009-November/202322.html") this to the mailing lists, with little success so far.)

---

### Post by colo on 2009-11-20
*push*

---

### Post by colo on 2009-11-25
One last try: *push*

---

