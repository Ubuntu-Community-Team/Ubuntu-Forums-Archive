---
title: "Totem MP3?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Branta on 2006-08-01
**Ubuntu 6.06 LTS - the Dapper Drake, Totem 1.4.1 supported by GStreamer 0.10.6 and Nautilus 2.14.1**

From terminal I installed this:
```
sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-ugly
```
so when I click on an MP3 audio CD, Sound Juicer plays the MP3 fine.

But when I click on an MP3 file on /dev/hda1 I get this error:
```
**Totem could not play file** that says:
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
```

So **How **and **What do I do**?

--- Bob ---

---

### Post by croak77 on 2006-08-01
Is  gstreamer0.10-fluendo-mp3 installed?

---

### Post by Branta on 2006-08-01
gstreamer0.10-fluendo-mp3 is [COLOR="Red"]*not installed*[/COLOR].

**Where** do I get it and **how** should I **install it**

--- Bob ---

---

### Post by croak77 on 2006-08-01
Open a terminal type;

sudo apt-get install gstreamer0.10-fluendo-mp3

---

### Post by Branta on 2006-08-01
Did I do something wrong?

```
sudo apt-get install gstreamer0.10-fluendo-mp3
Reading package lists... Done
Building dependency tree... Done
E: **[COLOR="Blue"]Couldn't find package gstreamer0.10-fluendo-mp3[/COLOR]**
```


--- Bob ---

---

### Post by Oxin on 2006-08-01
try opening synaptic package manager, clicking settings->repositories, and checking them all then try again.

---

### Post by mlind on 2006-08-01
install either gstreamer0.10-plugins-ugly or gstreamer0.10-fluendo-mp3.
You must have **universe** repository enabled.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by patrickthebold on 2006-08-02
I looks like you should be ok with the plugins...are you using totem-xine?

---

### Post by Branta on 2006-08-02
> **Oxin said:**
> try opening synaptic package manager, clicking settings->repositories, and **[COLOR="Blue"]checking them all then try again[/COLOR]**.

**That did it**!  Now on the Net when I click on an MP3 file it plays!

Thanks,

--- Bob ---

---

