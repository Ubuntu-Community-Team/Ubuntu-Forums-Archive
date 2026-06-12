---
title: "wxMaxima"
date: 2006-11-22
forum: Desktop Environments
---

### Post by bebop_tango on 2006-11-22
I'm having problems with wxMaxima again.

One of the very first things I did when I jumped from Dapper to Edgy was installing the wxmaxima package just to check if that 'famous' bug in Dapper was fixed. It worked wonders, but then something else happened just today.

The application wouldn't even start. This is what I got from the terminal:

```

$ wxmaxima
wxmaxima: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV9wxProcess' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV13wxJPEGHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV12wxPNGHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxComboBox' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV14wxImageHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV12wxXPMHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
wxmaxima: relocation error: wxmaxima: symbol _Z31_wx_link_dummy_func_gnome_printv, version WXU_2.6 not defined in file libwx_gtk2u_core-2.6.so.0 with link time reference

```

Well, I *think* this was due installation of gEDA Suite from the CD-ROM image I got... I remember the installation app asking me if I'd allow it to install wxWidgets for me, because it didn't find it on the system... so I let it... so I guess that caused the conflicts.

I tried to reinstall wxmaxima - along with the libwxgtk2.0 I tried uninstalling the package the installation app compiled, but 'make uninstall' didn't work at all - no target was found!

Any help...?

PS: xmaxima works. It must conflicts with the libwxgtk2.6-0 and libwxbase2.6-0 packages wxmaxima depends on... but how to fix it without reinstalling everything?

---

### Post by bebop_tango on 2006-11-23
I tried to recompile wxGTK but no good...

---

### Post by bebop_tango on 2006-11-23
Solved!

I installed these wxWidgets packages via Synaptic:

libwxbase2.6-0 (2.6.3.2.1.5)
libwxbase2.6-dev (2.6.3.2.1.5)
libwxgtk2.6-0 (2.6.3.2.1.5)
libwxgtk2.6-dev (2.6.3.2.1.5)
wx-common (2.6.3.2.1.5)
wx2.6-headers (2.6.3.2.1.5)

And ta-da! 

:D 

I couldn't uninstall the old wxGTK package built from source, but I suppose all the files it installed were just overwritten.

---

