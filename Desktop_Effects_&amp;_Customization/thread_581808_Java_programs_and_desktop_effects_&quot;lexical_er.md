---
title: "Java programs and desktop effects: &quot;lexical error or unexpected token&quot;"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by sarcangeli on 2007-10-19
Hi all,
I upgraded to Ubuntu 7.10 and enabled compiz effects.
When i try to execute a Java util that i use for working (Sonic Management Console, run on Sun JVM 1.5) it doesn't display any botton nor tabs, just opens an empty grey window. On the console output i have the following error displayed:

/usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: lexical error or unexpected token, expected valid token

Anybody knows if there's any way to solve this apart disabling compiz?

thanks!
Silvio

---

### Post by tonyarnold on 2007-11-04
> **sarcangeli said:**
> Hi all,
I upgraded to Ubuntu 7.10 and enabled compiz effects.
When i try to execute a Java util that i use for working (Sonic Management Console, run on Sun JVM 1.5) it doesn't display any botton nor tabs, just opens an empty grey window. On the console output i have the following error displayed:

/usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: lexical error or unexpected token, expected valid token

Anybody knows if there's any way to solve this apart disabling compiz?

thanks!
Silvio
This problem seems to be fixed if you use JVM 1.6, at least it does for me!

Regards,
Tony.

---

### Post by sarcangeli on 2007-11-11
Unfortunately my app doesn't support 1.6, so i tried going back to 1.4 instead. It worked!
thanks,
Silvio

---

