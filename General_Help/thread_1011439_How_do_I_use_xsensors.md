---
title: "How do I use xsensors?"
date: 2008-12-14
forum: General Help
---

### Post by amdalex on 2008-12-14
I installed Xsensors and when I go to Applications> System Tools> Xsensors all I get is a blanks windows that says Xsensors in the title bar.:confused:

---

### Post by amdalex on 2008-12-14
Anyone?

---

### Post by amdalex on 2008-12-14
Here is a screenshot of what I get.
[IMG]http://i152.photobucket.com/albums/s165/photoalexw/Screenshot-1.png[/IMG]

---

### Post by Slim Odds on 2008-12-14
Well, when I run it from the command line, I get this:
```
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

```

Looks like it needs some configuration.

---

### Post by tgalati4 on 2008-12-14
sudo apt-get install lm-sensors

sudo sensors-detect (answer yes to all the questions)

I like beagles.

---

### Post by amdalex on 2008-12-14
I already did that.

---

