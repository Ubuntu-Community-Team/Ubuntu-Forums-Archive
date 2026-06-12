---
title: "Turning off Screen Blanking"
date: 2005-05-03
forum: Desktop Environments
---

### Post by joedoc on 2005-05-03
Hello, all:

I'm having a great time with Hoary on a bunch of machines, but I have a question. I can't seem to figure out how to turn off the screen blanking in Ubuntu.

I have two systems affected, a Dell server with an ATI card, and a clone workstation with nVidia. I use Kubuntu on both. I want the KDE screensaver to hide the screen, but on both systems, the screen shuts off after a couple of minutes. 

The w/s uses ACPI, but not the server. I have searched through the configuration files on both systems and can't figure out where to turn this off. I'm sure it is something simple that I'm just not seeing.

Any advice?

Thanks.

---

### Post by Professor X on 2005-05-03
In you /etc/X11/xorg.conf there is a line that looks like this ```
Option     "DPMS"
```.  Comment out that line by putting a # in front  of it.  That should stopt he screen from blanking.

---

### Post by shakin on 2005-05-03
The BIOS also has settings for turning off the monitor. You might want to look there.

---

### Post by joedoc on 2005-05-03
Professor: found that. commented it out, we'll see what happens next time I start X,

Shakin: Thanks, looked there already. Nothing there, but thanks for the mention.

Thanks to both of you. I'll let you know what/if it works.

---

