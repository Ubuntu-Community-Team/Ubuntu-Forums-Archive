---
title: "How do I start programs with the system..."
date: 2010-05-24
forum: Desktop Environments
---

### Post by dougalkerr on 2010-05-24
I have just installed Ubuntu 10.4. I tried putting a few programs into the 'Startup Applications' but, for some reason they have not started with the system.
What should go into the 'Command' textbox. It is the only thing that I can have done wrong I think.
I simply browsed to the program file, e.g.;
/usr/share/applications/skype.desktop
I presumed this line would simply start Skype but, it didn't.
I did the same for Cairo dock and again it didn't start.

Any ideas?

---

### Post by Zemblan on 2010-05-24
In the commands box add the paths to the binaries themselves, not the .desktop. Most of these will be in /usr/bin. For example the command for skype is "/usr/bin/skype".
It should not be necessary to add the full path, just "skype" in the command box should work, because "/usr/bin/" is in your $PATH.

---

### Post by dougalkerr on 2010-05-24
Thanks Zemblan. Everything works as I want now. I had to add -c to the Cairo Dock to prevent OpenGL from loading coz it causes problems but, everything works now.

I just have to overcome the multiple monitors control problem and find a solution to the slow resizing of windows and I'll be a very happy chappy.

Cheers.

---

