---
title: "Problem with gdm and gdmgreeter"
date: 2007-11-13
forum: Desktop Environments
---

### Post by gorara on 2007-11-13
Hi, I've been having this problem with logging in to my box.  When I enter my username and password from the greeter it hangs for a while (sometimes alot) and finally loads the desktop.  A couple of times it just didn't load at all.  This is a section of my syslog:

```

cat /var/log/syslog.0 | grep gdm

Nov 13 01:15:52 xero gdm[6539]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed 
Nov 13 01:15:53 xero gdm[6539]: WARNING: gdm_slave_send: Can't open fifo! 
Nov 13 01:15:55 xero gdm[6539]: WARNING: gdm_slave_send: Can't open fifo! 
Nov 13 01:15:55 xero gdm[6539]: WARNING: gdm_slave_send: Can't open fifo! 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <debug/Enable=false> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value <FALSE> for <debug/Enable=false> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <greeter/GraphicalTheme=circles> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value <circles> for <greeter/GraphicalTheme=circles> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <greeter/GraphicalThemes=circles/:happygnome> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value <circles/:happygnome> for <greeter/GraphicalThemes=circles/:happygnome> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <greeter/GraphicalThemeDir=/usr/share/gdm/themes/> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value </usr/share/gdm/themes/> for <greeter/GraphicalThemeDir=/usr/share/gdm/themes/> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <gui/GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value </usr/share/themes/Default/gtk-2.0/gtkrc> for <gui/GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <gui/GtkTheme=Default> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value <Default> for <gui/GtkTheme=Default> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Could not access configuration key <greeter/Include=> 
Nov 13 01:15:59 xero gdmgreeter[6610]: CRITICAL: Using compiled in value <> for <greeter/Include=> 

```

I think maybe this is the cause of the hanging? I'm running Ubuntu 7.10 Gutsy.

Attached is a copy of the fully output...

---

