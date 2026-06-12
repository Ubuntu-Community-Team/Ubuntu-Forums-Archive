---
title: "How to prevent iphone from mounting? (8.10)"
date: 2009-02-04
forum: General Help
---

### Post by nbh on 2009-02-04
Ibex  8.10

I have a Vista VM and the sole purpose is for Apple iTunes.

When I attach my iPhone to my laptop, ubuntu automatically mounts the iPhone and I do not want that.

From [http://ubuntuforums.org/showthread.php?t=489841,I](http://ubuntuforums.org/showthread.php?t=489841,I) tried the following but the iPhone continues to be mounted and then it becomes a contest between ubuntu versus the Vista VM.

-------------
Edit file /etc/hal/fdi/preprobe/10-iphone.fdi:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
 <device> 
  <match key="usb.vendor_id" int="1452">
    <match key="usb.product_id" int="4752">
	<merge key="info.ignore" type="bool">true</merge>
    </match>
  </match>
 </device>
</deviceinfo>
```

Don't forget to "/etc/init.d/dbus restart", which will restart HAL so this change is picked up.
----------

Thanks.

---

### Post by lha on 2009-02-07
Have you checked that you are using correct usb.vendor_id and usb.product_id? Executing 'lshal> hal.txt' when your iPhone is attached will create a (largish) file in which you can find the correct ids.

---

