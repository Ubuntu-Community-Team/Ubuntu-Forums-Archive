---
title: "Can't run Brain Explorer with Wine"
date: 2008-02-02
forum: Education &amp; Science
---

### Post by orduek on 2008-02-02
I installed Allen's Brain Explorer 1.4 through wine.
after I checked it was supported. 
The Installation went smooth but i can't run it, it starts and fall without explanation.
anyone?

This is what I get when running with terminal:
[email]ord@ord-laptop:~/.wine[/email]/drive_c/Program Files/Allen Institute/Brain Explorer$ wine BrainExplorer.exe
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  158 (Composite)
  Minor opcode of failed request:  1 ()
  Serial number of failed request:  18
  Current serial number in output stream:  27

---

### Post by Dojan5 on 2008-02-04
This would do better in WINE forum i guess...

Not everything installed through WINE, even if it was successfully installed can be ran....
It can be a missing driver or something. I don't know, sorry...

---

### Post by machoo02 on 2008-02-04
Are you running compiz?  Try turning it off before running this program in Wine, and see if it makes a difference.

---

### Post by orduek on 2008-02-05
After turning off compiz. I get:
[email]or-metal@or-metal-desktop:~/.wine[/email]/drive_c/Program Files/Allen Institute/Brain Explorer$ wine BrainExplorer
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
DRM_I830_CMDBUFFER: -22

still no luck.
any ideas? the wine forums is empty.:(

---

