---
title: "HOW TO Add back/forward tap area in 8.10 Firefox Mini9"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ytsejam1138 on 2008-11-19
First, SHMConfig must be enabled.

In terminal type:

```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

Put this into the file:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
   <merge key="input.x11_options.LTCornerButton" type="string">8</merge>
   <merge key="input.x11_options.RTCornerButton" type="string">9</merge>
  </match>
</device>
</deviceinfo>
```
REBOOT NOW

This will allow you to tap the left top area of the trackpad to move back a web page in Firefox and to tap the right top area of the trackpad to move forward a web page in Firefox.

If you would like to use the bottom area of the trackpad, enter this code instead into shmconfig.fgi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
   <merge key="input.x11_options.LBCornerButton" type="string">8</merge>
   <merge key="input.x11_options.RBCornerButton" type="string">9</merge>
  </match>
</device>
</deviceinfo>
```

As far as I know this method only works in Firefox and only in Ubuntu 8.10 It is possible to do in Ubuntu 8.04, but I believe it involves editing the xorg.conf file instead of the the shmconfig.fdi

Also, this should work for any Dell computer that has a Synaptics trackpad.

---

