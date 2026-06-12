---
title: "Extra and Custom effects do not work with XGL+fglrx+Gutsy"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by schauerlich on 2007-12-04
I'm on an iMac (specs in signature) and I have XGL and fglrx installed and working. Compiz works, as the Normal effects can be enabled without problems. When I try to select Extra or Custom, it ticks it as it should. However, none of the effects are enabled. I can't get into ccsm, through the command line, System>Preferences>CompizConfig Settings Manager or Sys>Pref>Appearance>Visual Effects>Preferences. What's going on, and how do I fix it.

---

### Post by schauerlich on 2007-12-06
Bump.

---

### Post by mr. paperbox on 2007-12-07
I have excactly the same problem, ccsm doesn't work and so on... Also, when I'am using desklets, it gives this kind of log:

-------------------------------------------------------------------------------------------------------------
Log messages of /home/tiber/.gdesklets/logs/gdesklets%3A1.0.log                      
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is  
deprecated, use gtk.gdk.threads_init instead                                         
  gtk.threads_init()                                                                 
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module tiling: This Python has API version 1013, module tiling has      
version 1012.                                                                        
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module x11: This Python has API version 1013, module x11 has version    
1012.                                                                                
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module systray: This Python has API version 1013, module systray has    
version 1012.                                                                        
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/gdesklets-daemon:119: GtkDeprecationWarning: gtk.threads_enter is 
deprecated, use gtk.gdk.threads_enter instead                                        
  gtk.threads_enter()                                                                
-----------------------------------------------------------------------------------------------------------


Also compiz gave some errors about python. Could that be reason for this?

I have Ati Radeon 9550 and AMD +3000 & some ASRock.

---

