---
title: "java applications &amp; compiz problems"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by ashwin_cse on 2007-06-25
There seems to a problem with java application (in my case limewire) accessing the display. Limewire for example displays only the window border & does not show the contents of the windows. This happens only when the desktop effects are active. When the desktop-effects are switched off limewire behaves normally. Is there any other work-around other swtiching off desktop-effects? Since i like both desktop-effects & limewire.

--ashwin

---

### Post by akshayas1986 on 2007-06-26
Buddy
This is a bug.. Happens with Limewire or frostwire..

Write this script file and execute this to open you P2P app (Limewire or frostwire)

> #!/bin/sh
export AWT_TOOLKIT="MToolkit"
export HOSTNAME=localhost
/usr/bin/frostwire    #This is the location of frostwire executable.. Locate where your limewire executable put   
                               #the full path up here 

Akshaya Srivatsa

---

