---
title: "VMWare Server Console without themes on Gutsy"
date: 2007-10-25
forum: Desktop Environments
---

### Post by rev3nant on 2007-10-25
VMWare Server Console somehow starts unthemed and looking very ugly on Gursy x64. Happens with any theme.

Getting errors similar to this:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:42: error: unexpected character `@', expected string constant

Probably started after some lib update. Any thoughts greatly appreciated. :(

---

### Post by swerling on 2007-12-08
I got the exact same error. I recently upgraded all the way from Dapper to Gutsy. 

The first two error messages can be cured with these 2 lines:
  sudo ln -s /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
  sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

I still get the 3rd error message:

/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:42: error: unexpected character `@', expected string constant.

I'm stuck there.

---

