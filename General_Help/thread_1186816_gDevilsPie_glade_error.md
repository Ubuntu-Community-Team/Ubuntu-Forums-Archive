---
title: "gDevilsPie glade error"
date: 2009-06-13
forum: General Help
---

### Post by the real omni on 2009-06-13
I followed the link for the gDevilsPie download on this page: [http://ubuntuforums.org/showthread.php?t=741993]("http://ubuntuforums.org/showthread.php?t=741993")

I was able to run the .deb just fine, but when I run gdevilspie I get the following error:


Glade file not found, exiting.


Can anyone tell me how to fix this?

---

### Post by wecucho on 2010-06-03
Hi, i just have the same problem, i fix the problem by editing gdevilspie python file, you can follow this steps:

1.- Download 'gdevilspie-0.31.tar.bz2' from google project.
2.- edit the file 'gdevilspie' find the line '# Glade file used in all classes' and add the following code JUST BEFORE the if block:

if os.path.isfile('gdevilspie.glade'):
        gladefile = 'gdevilspie.glade'
el

NOTE that the 'el' at the end will make another elif sence.

Then find the line '# icon used' and add the following code JUST BEFORE the if block:

if os.path.isfile('gdevilspie.png'):
        gdevilspie_icon = 'gdevilspie.png'
el

3.- Finally run again your gdevilspie, it should be working 'python gdevilspie'

Regards,

---

