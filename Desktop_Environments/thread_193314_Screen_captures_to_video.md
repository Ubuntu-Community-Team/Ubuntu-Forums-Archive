---
title: "Screen captures to video?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by illynova on 2006-06-09
Hey guys,

I've been looking around, and so far no luck. What program(s) would I want to use if I needed to capture the actions on my screen in  a video?

Looking around, the only program I can find is xvidcap, but I cannot seem to locate any AMD64 packages for dapper.

scott@blackmarsh:~$ sudo apt-get install xvidcap
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xvidcap


apt-cache turns up nothing useful

---

### Post by Rondonjin on 2006-06-09
[QUOTE=illynova]Hey guys,

I've been looking around, and so far no luck. What program(s) would I want to use if I needed to capture the actions on my screen in  a video?

Looking around, the only program I can find is xvidcap, but I cannot seem to locate any AMD64 packages for dapper.

scott@blackmarsh:~$ sudo apt-get install xvidcap
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xvidcap


apt-cache turns up nothing useful[/QUOTE]

Two I know of are Istanbul and Byzanz. I don't know if they're available for AMD64.

Wayne

---

### Post by userundefine on 2006-06-10
I don't see xvidcap in any repos on plain ol' x86.

---

### Post by gspr on 2006-06-10
I don't know if it's exactly what you're looking for, but [vnc2swf]("http://www.unixuser.org/~euske/vnc2swf/") is a program that records a VNC session to Flash. I sure wish it would use something other than Flash, but I guess it's better than nothing.

---

### Post by userundefine on 2006-06-27
A Windows and proprietary program?  No thanks...

---

### Post by ronb on 2006-07-05
[QUOTE=illynova]Hey guys,

I've been looking around, and so far no luck. What program(s) would I want to use if I needed to capture the actions on my screen in  a video?

Looking around, the only program I can find is xvidcap, but I cannot seem to locate any AMD64 packages for dapper.

[/QUOTE]

I'm trying to install [[COLOR="Navy"]**xvidcap**[/COLOR]]("http://xvidcap.sourceforge.net/"), but I need to compile it from source. So that's going to take me a while to figure out. I also looked into [[COLOR="Navy"]**vnc2swf**[/COLOR]]("http://www.unixuser.org/~euske/vnc2swf/"), but the audio from the web site's examples don't work in my Firefox and Dapper. And I haven't spent much time trying to fix that yet. I installed the latest Firefox plug-in. I know that sometimes Audacity won't work either if I have system sounds enabled in my Gnome preferences.

A third option that I'm going to look into when I get a chance is [[COLOR="Navy"]**Wink**[/COLOR]]("http://www.debugmode.com/wink/"). I don't know how it works, and I don't know if there are binaries for Ubuntu. So I might need to compile that too.

---

