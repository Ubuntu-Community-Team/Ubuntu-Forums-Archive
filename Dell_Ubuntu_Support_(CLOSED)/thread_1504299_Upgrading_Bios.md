---
title: "Upgrading Bios"
date: 2010-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gabo.cr on 2010-06-07
I have a Dell Inspiron 1525, I only have Ubuntu 10.04 in it.
How can I upgrade the Bios?
I was reading on how to do it, but it takes Window$ to do it.
Is there anyway to do this with Ubuntu?
The reason is to activate the bluetooth.
Any help will be appreciated.

---

### Post by DavePlummer on 2010-06-07
I recently updated the BIOS on a Dell Inspiron 1545, using the instrucions at _[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)_ []("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate"). They worked flawlessly.

---

### Post by gabo.cr on 2010-06-11
Thank you!
I will try it.

---

### Post by gabo.cr on 2010-06-11
I did it, but I'm getting this:

> Performing BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 185, in <module>
    sys.exit( main() )
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_update.updateBios at 0x0970687C>", line 3, in updateBios
  File "/usr/lib/python2.6/dist-packages/libsmbios_c/trace_decorator.py", line 98, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.6/dist-packages/libsmbios_c/rbu_update.py", line 96, in updateBios
    raise InappropriateHDRFile( _("The system bios version (%s) is the same as or newer than the .HDR file (%s).") % (ver, hdrfile.biosVersion()) )
libsmbios_c.rbu_update.InappropriateHDRFile: The system bios version (A13) is the same as or newer than the .HDR file (A13).


Does that mean that the Bios on my computer already has the latest update?
:-s

---

### Post by mr clark25 on 2010-06-11
> **gabo.cr said:**
> I did it, but I'm getting this:



Does that mean that the Bios on my computer already has the latest update?
:-s

look at part of the last line in the quote:
> The system bios version (A13) is the same as or newer than the .HDR file (A13). 			 		

im no expert, but doesn't that mean you are trying to install the same version that you already have installed?

---

### Post by gabo.cr on 2010-06-13
> im no expert, but doesn't that mean you are trying to install the same version that you already have installed?

Yes, I was installing the same version!! ](*,)

I updated to the latest version now (A17).
Thank you.
:biggrin:

---

