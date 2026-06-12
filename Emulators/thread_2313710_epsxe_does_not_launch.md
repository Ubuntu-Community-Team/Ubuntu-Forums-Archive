---
title: "epsxe does not launch"
date: 2016-02-15
forum: Emulators
---

### Post by MattKimura on 2016-02-15
For years now, I've never been able to execute epsxe. I downloaded v1.9.25 for linux, unzipped it into a folder, enabled the executable to run as a program. But nothing happens when I execute it. What exactly are the dependencies for this emulator?

I ran sudo apt-get update && sudo apt-get upgrade

For some reason, not even pcsxr opens up, it says "failed to open directory pcsxr". 
I'm not sure what I'm missing, I tried googling for an hour. I really need some support.

I'm running Xubuntu

---

### Post by MikeCyber on 2016-02-15
Never heard of but:
ldd myexecutablename
after
cd /path/to/my/app
in a terminal should display dependencies.
Even ./myecexutable should give you hints.

---

### Post by deadflowr on 2016-02-15
Moved to** Emulators**

---

### Post by MattKimura on 2016-02-15
> **MikeCyber said:**
> Never heard of but:
ldd myexecutablename
after
cd /path/to/my/app
in a terminal should display dependencies.
Even ./myecexutable should give you hints.

It tells me that it's not a dynamic executable. 
But I already found the right dependencies after hours of searching. I can finally open it's GUI, but now I'm stuck on what plugins I need for it. For Windows it was as simple as dragging and dropping the plugins. But for linux you have to compile the plugins, which I'm shaky with for the most part. 
Any idea what plugins to use?


For anyone else wondering about dependencies:

[LIST]
[*][COLOR=#333333]sudo apt-get update && sudo apt-get upgrade[/COLOR]

[*][COLOR=#333333]sudo apt-get install libsdl-ttf2.0-0:i386[/COLOR]

[*][COLOR=#333333]sudo apt-get install gtk2-engines:i386[/COLOR]

[*][COLOR=#333333]sudo apt-get install libgtk2.0-0:i386[/COLOR]
[/LIST]

---

