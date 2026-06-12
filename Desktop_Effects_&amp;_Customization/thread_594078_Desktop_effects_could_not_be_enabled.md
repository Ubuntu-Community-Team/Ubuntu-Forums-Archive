---
title: "Desktop effects could not be enabled"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by pranksta on 2007-10-27
PROBLEM SOLVED BY DISABLING RESTRICTED DRIVERS



Hi,

I've been an avid user of ubuntu since Hoary, but i have had nothing but problems with my video card which is a Radeon 9700 Mobility.
I'd been having a problem in 7.04 enabling my desktop effects so i chose not to enable them at all and stick with a a basic desktop. I have used Beryl before and loved it but as any normal linux user i like to tweak and often mess things up.
When trying to enable desktop effects in 7.10 i get the error message "Desktop effects could not be enabled".
Below is the output when i try to run compiz in terminal.

<<START OF LOG>>
comlee@lee-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
<<END OF LOG>>

I'm lost as to what the problem is, i have viewed many threads on these very forums but have not yet been able to find a solution.

If there is anYbody out there who can help me out, i would greatly appreciate it.

Regards,

Pranksta

---

### Post by itsbradman on 2007-10-27
Were you able to get the effects working with compiz fusion in Feisty?

---

### Post by itsbradman on 2007-10-27
Also, please post the output of fglrxinfo and glxinfo.

---

