---
title: "Azureus / Vuze - How can multiple users run their own instance???"
date: 2009-01-06
forum: Desktop Environments
---

### Post by coloradogiant on 2009-01-06
Hello,

I have followed a tutorial on this site and got Vuze 4.0 installed and working great (for one user....)

Is there a way to allow vuze to exist as seperate instances for multiple users logged in at the same time?

Scenario: 3 users are logged into Ubuntu all using NoMachine VNC. Each has their own desktop. When user #1 launches Vuze, users #2 and #3 can't. Vuze can apparently only exist for one user per machine?

Anyway to get this working?

---

### Post by caowm on 2009-06-28
hello
you know vuze checks 127.0.0.1:6880 to determine if there is another instance.
there is an option to allow multiple instances,

```
java --cp /usr/share/java/Azureus2.jar:/usr/share/java/swt-gtk-3.4.jar -DMULTI_INSTANCE=true org.gudy.azureus2.ui.common.Main
```

please see this
[http://www.azureuswiki.com/index.php/Commandline_options#Path_Options](http://www.azureuswiki.com/index.php/Commandline_options#Path_Options)

I had a try and find it works.
I'm not sure whether it would cause any issues.
you'd better be careful

---

