---
title: "autorun"
date: 2009-04-03
forum: General Help
---

### Post by wounded cheezie on 2009-04-03
my cds and downloads  are not starting with autorun prompt..  i get an error  message  cannot find autorun program. 

    Like, whats up .....assistance with this matter would be greatly admired     
   
     thanxz     wounded cheezie.. :guitar:):P

---

### Post by schmidtbag on 2009-04-03
I'm not sure about other distros but I do know Ubuntu does not run wine at autorun.  Autorun is designed for linux programs, not windows.  I'm aware that makes the feature nearly entirely pointless but theres probably going to be some update some day that allows wine to be used at autorun.

---

### Post by 3rdalbum on 2009-04-03
Windows programs will not run automatically even if they set as the Windows autorun on a CD. They're Windows programs, after all.

You may be able to get *some* Windows programs to work on Ubuntu by use of some software called Wine, which is available from the Synaptic Package Manager, but the best solution is to find equivalent software for Linux.

---

### Post by 3rdalbum on 2009-04-03
> **schmidtbag said:**
> I'm aware that makes the feature nearly entirely pointless but theres probably going to be some update some day that allows wine to be used at autorun.

Magazine coverdiscs often set HTML files as autorun, if they have an HTML directory of the disc's contents.

---

### Post by kanikilu on 2009-04-03
Run gconf-editor and browse to apps > nautilus > preferences. Make sure media_autorun_never is not checked.

---

### Post by ariedry on 2009-04-03
Thanks its realy helpful ^^

---

### Post by wounded cheezie on 2009-04-03
so what and where do i get the program that runs or opens downloads from the web..?

  ya  ?:confused:

---

### Post by schmidtbag on 2009-04-04
what specifically have you downloaded?  if its a tar.gz or .tgz then you have to extract and compile it.  if its a .deb it should just run.  if its an .rmp you have to use alien and convert it.

---

