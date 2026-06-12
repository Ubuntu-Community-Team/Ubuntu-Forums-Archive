---
title: "how do you know what X extensions are available?"
date: 2009-04-21
forum: General Help
---

### Post by cyran on 2009-04-21
Is there's a command-line tool that prints what X extensions are enabled or disabled, or lists what's supported with the current X server version / graphics driver?

There should be some way to know, since Compiz can check for Compositing before it turns on.

---

### Post by ajmorris on 2009-04-22
> **cyran said:**
> Is there's a command-line tool that prints what X extensions are enabled or disabled, or lists what's supported with the current X server version / graphics driver?

There should be some way to know, since Compiz can check for Compositing before it turns on.

Hi there,
to check what extensions are being loaded at X startup, you can run the following command:
```
cat /var/log/Xorg.0.log | grep -i extensions
```
That will grep your xorg log file for the search term 'extensions' (case insensitive because of the -i paramater on grep) and print out to stdout (your terminal output) what it finds.
For checking what is supported, you can run ```
glxinfo
``` and take a look through that at what glx (server and client) extensions are supported, and what opengl extensions are supported.

AJ

---

