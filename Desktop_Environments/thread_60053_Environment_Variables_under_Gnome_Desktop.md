---
title: "Environment Variables under Gnome Desktop"
date: 2005-08-26
forum: Desktop Environments
---

### Post by twelvegates on 2005-08-26
How can one set personal envirnment variables under the Gnome desktop if the Gnome-session is launched by GDM?
The variables should be visible for applications launched by the Run Applicatoin dialog rather than only for applications launched in a shell-terminal window.

I have set an environment variable in ~/.profile. But this seems not to be effective in the Gnome desktop.

---

### Post by amohanty on 2005-08-27
Did you try puttin it in the ~/.login

AM

---

### Post by twelvegates on 2005-08-27
[QUOTE=amohanty]Did you try puttin it in the ~/.login[/QUOTE]

No.
My login shell is */bin/bash*. ~/.login is not used by bash nor does it occur in the bash manpage.
~/.login is used by *csh* and *tcsh*.

By the way: this behaviour also seems to occur in Debian.
But it doesn't occur in Fedora Core 4 and FreeBSD.
So it's a bug of Debian and Ubuntu.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14206](http://bugzilla.ubuntu.com/show_bug.cgi?id=14206)

---

### Post by amohanty on 2005-08-27
Look for default.session and put it in there. If you want it on a per user basis you will need to setup a session via System->Preferences->Sessions.

---

### Post by twelvegates on 2005-08-27
~/.gnomerc may be used to set environment variables.

[http://gnomesupport.org/forums/viewtopic.php?t=9841](http://gnomesupport.org/forums/viewtopic.php?t=9841)

---

