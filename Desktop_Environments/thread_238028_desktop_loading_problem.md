---
title: "desktop loading problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by somi38 on 2006-08-17
i changed my monitor,when i start ubuntu all kind of loading successfully completed.but when ubuntu ask us about username & password this page is not loaded .and monitor screen is completely black and nothing to do

any one knoww about this error please tell me

---

### Post by hecato on 2006-08-17
Basically X server start OK (gdm logon screen is show), but when entering it stay black (and the led-of monitor blink indicating a bad resolution or rate).


Here is an answer related to that [http://ubuntuforums.org/showpost.php?p=1388643&postcount=14](http://ubuntuforums.org/showpost.php?p=1388643&postcount=14)

... that is

[LIST]
[*]Try switching with CTRL+ALT+"+" or "-" (switch monitor resolution)
[*]Try to see the correct range of the monitor and set it on xorg.conf file, then restart the X server and see if work
[*]Ckeck always the available modes with **xrandr**... also note that sometimes switching with the combination of keys will not work properly and you should try set it with **xrand -s XPixels**x**YPixels -r ValidRate**.[/LIST]That is explained more "in depth" in the anterior link...

See if this help.

---

### Post by somi38 on 2006-08-17
then link you given to me is for amd64 i have system i386
please tell me what i do

---

