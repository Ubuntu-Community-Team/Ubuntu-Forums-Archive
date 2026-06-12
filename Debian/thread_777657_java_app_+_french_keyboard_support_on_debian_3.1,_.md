---
title: "java app + french keyboard support on debian 3.1, console (not X)"
date: 2008-05-01
forum: Debian
---

### Post by devi8 on 2008-05-01
Hi,
 I have done all that is required to enable french locale on the console,  on debian as root. i.e installed console-tools, use loadkeys, installkeys. and locale shows me that french locale is available. I am also able to input from french keyboard (or US keyboard using Alt Shift), and I can see that the terminal console, displays the french keys correctly.
  However, any java swing application run from this env, doesnt seem to work with the french keyboard. IT treats it as a english keyboard. I have set the variable LC_CTYPE to fr_FR.UTF-8. 
  I am able to make the same app work on redhat4.6 without doing anything, just a regular full install makes this work, along with LC* settings.

  So, pls advice me what is needed from debian side to make the java app work with french keyboard in console mode (i.e non-X mode).
  

Thanks,
uma

---

