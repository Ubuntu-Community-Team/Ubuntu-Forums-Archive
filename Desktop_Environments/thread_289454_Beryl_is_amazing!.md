---
title: "Beryl is amazing!"
date: 2006-10-31
forum: Desktop Environments
---

### Post by Paradoxdruid on 2006-10-31
After upgrading to Edgy, I thought I'd try to bring my Kubuntu into the 21st centruy, and finally give Beryl a try...

In Edgy, the process is completely painless and had no errors--  I'm using two monitors on a single nVidia card with TwinView, and it detected and configured everything just right, with no intervention from me.

And now...  my windows wobble, I have a desktop cube, opacity at full speed, and OSX-like Expose behavior.

*happy sigh*

After dealing with the debconf in kubuntu debacle to get Edgy installed, Beryl installation was a breath of fresh air.

---

### Post by YoungGods on 2006-11-02
hi there, I want to give Beryl a try in Kubuntu Edgy (used it in Dapper), can you please point me to a good how-to ? 
thanks

---

### Post by bluenova on 2006-11-02
It sure is amazing, I just wish I could switch users without having to go back to metacity first.

[Install guide for Nvidia](http://ubuntuforums.org/showthread.php?t=263851) worked like a charm for me.

---

### Post by Paradoxdruid on 2006-11-02
> **YoungGods said:**
> hi there, I want to give Beryl a try in Kubuntu Edgy (used it in Dapper), can you please point me to a good how-to ? 
thanks

I followed the official How-to on the Beryl Project Wiki:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

Essentially, you add a line to your apt-sources, and then:```
sudo apt-get update
sudo apt-get install beryl beryl-core beryl-plugins beryl-plugins-data \
beryl-settings beryl-manager emerald emerald-themes xserver-xgl
```

Followed by making a start-up file (with very good directions).

Enjoy!

---

