---
title: "Frustrated with HAL, FDI ignoring xorg"
date: 2009-01-26
forum: General Help
---

### Post by dardack on 2009-01-26
Ok so I have 8.10, but had no clue that it ignores options in xorg.conf now (just found this out), so I can invert my y axis on my mouse like I like to when playing games that do not have this option.  I have tried to create an FDI but it doesn't work:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" contains="mouse">
   <merge key="input.x11_options.InvY" type="string">true</merge>
  </match>
 </device>
</deviceinfo>

```


Need some help please.

---

### Post by dardack on 2009-01-26
Anyone?

---

### Post by dardack on 2009-01-26
Ok I've changed:

```
<merge key="input.x11_options.InvY" type="string">true</merge>

```

to:

```
<merge key="input.x11_options.InvY" type="bool">true</merge>

```

now when I run lshal i get:

```
 input.x11_driver = 'synaptics'  (string)
  input.x11_options.InvY = true  (bool)

```

and:

```
< 
< udi = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0_logicaldev_input'
<   info.capabilities = {'input', 'input.mouse'} (string list)
<   info.category = 'input'  (string)
<   info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0'  (string)
<   info.product = 'Logitech USB Receiver'  (string)
<   info.subsystem = 'input'  (string)
<   info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0_logicaldev_input'  (string)
<   input.device = '/dev/input/event11'  (string)
<   input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0'  (string)
<   input.product = 'Logitech USB Receiver'  (string)
<   input.x11_driver = 'evdev'  (string)
<  [SIZE="6"] input.x11_options.InvY = true  (bool)[/SIZE]
<   linux.device_file = '/dev/input/event11'  (string)
<   linux.hotplug_type = 2  (0x2)  (int)
<   linux.subsystem = 'input'  (string)
<   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input12/event11'  (string)

```

Ok so it's in there, but neither my touchpad or my mouse is inverted.  It's freaking annoying as hell.

---

### Post by dardack on 2009-01-27
New day, new bump.  Can't figure it out.  Or if anyone knows a better place (mailing list, forum, etc) to post this that'd could help too.

---

### Post by dardack on 2009-01-29
New day new bump.

---

### Post by Nepherte on 2009-01-29
I'd stick with using string instead of bool. Mine are all strings and they work. After you changed the fdi file, did you restart your computer or restarted the hall service?
```
sudo /etc/init.d/hal restart
```

---

### Post by dardack on 2009-01-29
> **Nepherte said:**
> I'd stick with using string instead of bool. Mine are all strings and they work. After you changed the fdi file, did you restart your computer or restarted the hall service?
```
sudo /etc/init.d/hal restart
```

I'll try that, from the documentation (what little there is) i found that hal doesn't need to be restarted just the device unplugged replugged.  Also, I have restarted my computer with both bool and string and both show up in the lshal command, it just wont' invert the y axis.

---

