---
title: "Upgrading Firefox 1.0.2 to 1.0.6 via source and a system monitor tool?"
date: 2005-07-26
forum: Desktop Environments
---

### Post by erik-the-red on 2005-07-26
1. I have Firefox 1.0.2 installed on my Ubuntu Hoary system. It's the one that came with the default install.

I don't think it's coded very well because when I used Firefox on Windows 2000, it did not consume 105.5mb of "VM Size." I obtained that number through the GNOME System Monitor.

How do I "upgrade" to 1.0.6 from source?

2. What is the most popular system monitor tool? I've seen it in a lot of screenshots. It displays CPU usage, memory usage, and so forth, and it looks cool. Sorry for being vague.

Thanks in advance.

---

### Post by norman_h on 2005-07-26
I find that the most versitile system monitor is top.  It can be run from the command line.  It is a text based program and is not a GUI program.

---

### Post by ubuntp on 2005-07-26
1.06 or 1.02 it won't make a difference in memory size, that's only the virtual memory being used anyway, not the *real*  memory being used. A more or less accurate number would be the RES field you can see using top. Here my RES for Firefox is being reported as 42MB, while the VM is 115MB. UNIX/Linux memory system is quite complex and it's not so easy to figure out how much memory is really being used.

You can also add the field in the Gnome System Monitor by activating non paged memory in the preferences.

---

### Post by pataphysician on 2005-07-26
in response to question #2, the utility you're referring to is probably gkrellm. you can install it via synaptic. plugins and skins are available here

[http://www.muhri.net/](http://www.muhri.net/)

---

### Post by erik-the-red on 2005-07-27
[QUOTE=pataphysician]in response to question #2, the utility you're referring to is probably gkrellm. you can install it via synaptic. plugins and skins are available here

[http://www.muhri.net/](http://www.muhri.net/)[/QUOTE]
 Pataphysician, that is exactly the program I'm looking for. Thanks!

---

### Post by erik-the-red on 2005-07-30
[QUOTE=erik-the-red]Pataphysician, that is exactly the program I'm looking for. Thanks![/QUOTE]
 I'm still interested in upgrading from 1.0.2 to 1.0.6

Exactly how would I do this given that I'm using 1.0.2 now and that I have the source for 1.0.6?

---

