---
title: "Stopping XGL"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by rectec794613 on 2008-03-26
I just installed Xserver-XGL and logged off then back on.
The problem is that its a TOTAL RESOURCE HOG:(
The program isn't even running! The only thing running is the process.
Which brings me to another question. WHY DOES IT SAY I'M USING 200 MB of memory? Take a look at this: [IMG]http://www.watchingthenet.com/wp-content/uploads/image/ubuntusysmonitor4.png[/IMG](Note: These are not my processes)
And Take a look at this: [IMG]http://members.home.nl/jeroen-91/ubuntu/breezy-new/system-monitor.png[/IMG](not my resources)

OK, only a few Mb used from processes but it says its using 200 something MiB!

WHY?:confused:

---

### Post by unoodles on 2008-03-26
yes the XGL server does take alot of cpu.

I dont think that it is anything to be worried about concerning RAM usage.
i use 800mb when idle

---

### Post by rectec794613 on 2008-03-26
> **unoodles said:**
> yes the XGL server does take alot of cpu.

I dont think that it is anything to be worried about concerning RAM usage.
i use 800mb when idle

My Main Concern is the deal with XGL... I want to stop it](*,)<XGL

---

### Post by unoodles on 2008-03-26
So uninstall the XGL package (sudo apt-get remove xserver-xgl --purge)

then restart X (ctrl+alt+backspace)

---

