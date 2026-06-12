---
title: "Good kernel source"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Vertical on 2005-11-05
I want to recompile my Ubuntu's kernel

Where I can get ubuntu's kernel source for i386? As I understand, there are swsusp and many other patches (maybe acpi, etc..). I will be great if I can find patched kernel source.

What option should present in kernel, except swsusp (it must be) :) for the normal system work after compilation

Thanks

---

### Post by kvidell on 2005-11-05
[QUOTE=Vertical]I want to recompile my Ubuntu's kernel

Where I can get ubuntu's kernel source for i386? As I understand, there are swsusp and many other patches (maybe acpi, etc..). I will be great if I can find patched kernel source.

What option should present in kernel, except swsusp (it must be) :) for the normal system work after compilation

Thanks[/QUOTE]
> linux-source-2.6.12 - Linux kernel source for version 2.6.12 with Ubuntu patches.Soo... I believe something as simple as:
sudo apt-get install linux-source-2.6.12
will get you what you need.

I'm not sure what your second question is referring to, though. Rephrase?
- K

---

### Post by poofyhairguy on 2005-11-05
Moving to correct forum - no questions here please.

---

### Post by az on 2005-11-05
Install linux-tree and you are good to go.  I think it already comes with the default configuration.  Otherwise, you need to get your current config from /boot.


Why do you need to recompile your kernel?

---

### Post by kvidell on 2005-11-05
[QUOTE=azz]Install linux-tree and you are good to go.  I think it already comes with the default configuration.  Otherwise, you need to get your current config from /boot.


Why do you need to recompile your kernel?[/QUOTE]
I sometimes do because I've naught else to do...
It's fun if you use the -j2 flag on the actual build :) (I can't get your dpkg method to work :-\ It seems more solid, but it disagrees with me)
- K

---

### Post by Kyral on 2005-11-05
Now the question is how you would apply the Ubuntu patches to the 2.6.14 sources from Kernel.org

---

