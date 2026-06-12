---
title: "Dell Bios Update fails."
date: 2009-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chinoy on 2009-09-10
**If I try dellBiosUpdate  -u -f ./bios.hdr**

root@laptop:~/Desktop# dellBiosUpdate  -u -f ./bios.hdrPerforming BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 185, in <module>
    sys.exit( main() )
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_update.updateBios at 0x09A046BC>", line 3, in updateBios
  File "/usr/lib/python2.5/site-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.5/site-packages/libsmbios_c/rbu_update.py", line 96, in updateBios
    raise InappropriateHDRFile( _("The system bios version (%s) is the same as or newer than the .HDR file (%s).") % (ver, hdrfile.biosVersion()) )
libsmbios_c.rbu_update.InappropriateHDRFile: The system bios version (A12) is the same as or newer than the .HDR file (A05).

**If I try : dellBiosUpdate --override_bios_version -u -f ./bios.hd**
root@laptop:~/Desktop# dellBiosUpdate --override_bios_version -u -f ./bios.hdr
Usage: smbios-rbu-bios-update

dellBiosUpdate: error: no such option: --override_bios_version

I tried with one - I tried with replacing with my existing bio nothing nada
why cant things just work !!!!:confused:

---

### Post by chinoy on 2009-09-12
Bump Please help

---

### Post by maghajan on 2009-09-24
Bump!  I have this same problem.  I am following the instructions on this page:  [http://www.ducea.com/2007/08/27/dell-bios-firmware-updates-on-debian/](http://www.ducea.com/2007/08/27/dell-bios-firmware-updates-on-debian/)

Any help is greatly appreciated!!! 

OUTPUT:

$ sudo dellBiosUpdate -u -f bios.hdr
Performing BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 185, in <module>
    sys.exit( main() )
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_update.updateBios at 0x0250F398>", line 3, in updateBios
  File "/usr/lib/python2.5/site-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.5/site-packages/libsmbios_c/rbu_update.py", line 95, in updateBios
    if compareBiosVersions(ver, hdrfile.biosVersion()) >= 0:
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_hdr.biosVersion at 0x024CCC08>", line 3, in biosVersion
  File "/usr/lib/python2.5/site-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.5/site-packages/libsmbios_c/rbu_hdr.py", line 86, in biosVersion
    ver = "%d.%d.%d" % struct.unpack("BBB", self.hdr.biosVersion)
NameError: global name 'struct' is not defined

---

### Post by gliverman on 2009-11-13
Bump. I have the same problem.

```
# dellBiosUpdate -u -f ./bios.hdr
Performing BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 185, in <module>
    sys.exit( main() )
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_update.updateBios at 0x018C9DE8>", line 3, in updateBios
  File "/usr/lib/python2.5/site-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.5/site-packages/libsmbios_c/rbu_update.py", line 95, in updateBios
    if compareBiosVersions(ver, hdrfile.biosVersion()) >= 0:
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_hdr.biosVersion at 0x01906488>", line 3, in biosVersion
  File "/usr/lib/python2.5/site-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.5/site-packages/libsmbios_c/rbu_hdr.py", line 86, in biosVersion
    ver = "%d.%d.%d" % struct.unpack("BBB", self.hdr.biosVersion)
NameError: global name 'struct' is not defined
```

This is a fresh Ubuntu 9.10 x64 setup on a Dell Optiplex 745.

---

### Post by Zoot7 on 2009-11-13
Quick question; why do you all want to even update the BIOS?
Unless there's a new feature offered such as new support for a CPU you want to use, it's recommended not to touch the BIOS especially on OEM machines on account of having no BIOS recovery tool.

Anyway, I could be mistaken but afaik It's possible to boot into a DOS envoirnment and run the executable provided by Dell to update the bios that way.

---

