---
title: "blank window with jconsole and desktop effects"
date: 2007-04-18
forum: Desktop Effects &amp; Customization
---

### Post by fwendt on 2007-04-18
Hi. I only get window borders/decorations when I run jconsole (or "Sun Java 6 Console"). This only happens when Desktop effects are turned on - when it's off things work as expected.
Is there anything I can do except to turn Desktop effects off when launching the application?

To try yourself, simply install sun-java6-sdk and run jconsole:
```
sudo aptitude install sun-java6-jdk
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/jconsole
```

---

### Post by justinlindh on 2007-04-18
I run into this problem with Netbeans (which runs in a JRE, also). I believe that this has been fixed with JDK 1.6.0_01, which was recently released. I noticed a bullet in the changelog about compiz, installed it, launched Netbeans, and the problem disappeared.

Unfortunately, JDK6 seems to force the GTK Look and Feel, which doesn't work well in Netbeans IMO. So I'm sticking with JRE 1.5.0_11, and I simply have to toggle "Enable GL Desktop" in the "System -> Preferences -> GL Desktop" dialog. Once the app is running, if you toggle Compiz/Beryl off/on it will render the window properly. Unfortunately, this also leads to lost window handles on occasion, and some apps refuse to take input until restarted (for example, if you disable/enable GL Desktop with a terminal open, around 50% of the time you'll need to kill the terminal as it won't allow you to type into it anymore). Chalk these issues up to Compiz bugs, though.

---

