---
title: "Control Center and &quot;Administrator mode&quot;"
date: 2005-04-11
forum: Desktop Environments
---

### Post by hyde on 2005-04-11
I have problems with KDE's Control Center. When I try to set my networking cards etc. I click the "Administrator mode" button. Then it asks my password and after that it just jumps to the Control Center's opening screen and won't let do any changes. Well, ofcourse it worked just a minute ago when I tried it, but usually it doesn't work properly...

---

### Post by dermotti on 2005-04-11
Hmm, i had that issue, only way i found around it was activating the root account...

---

### Post by weeguy on 2005-04-11
[QUOTE=dermotti]Hmm, i had that issue, only way i found around it was activating the root account...[/QUOTE]
 well... i used    sudo kcontrol    and it works too..

---

### Post by dermotti on 2005-04-11
DO you have to sudo kcontrol from commandline?

---

### Post by weeguy on 2005-04-11
[QUOTE=dermotti]DO you have to sudo kcontrol from commandline?[/QUOTE]
 Yes, but only to access certain areas of Control Center that require "Administrator Mode"

---

### Post by buldir on 2005-04-11
I had the same problem.  I reinstalled the OS and all was fine.  Or, like the others have said, while typing your password, the dialog box shows you the command you're running, so just manually use sudo and the command line.

---

