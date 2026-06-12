---
title: "forever to load gedit."
date: 2005-12-30
forum: General Help
---

### Post by drfalkor on 2005-12-30
When I type 'gedit', in the konsole - it's taking forever to load it up, like over 5 min.
I have the same "problem" with anjuta.
I havent tryed to reboot, but - you don't need to reboot linux?

---

### Post by manubreizh on 2005-12-30
hi,
for editing and modifying files, you can use kedit (which must be faster) or vim (type vi the_file_you_want_to_modify in konsole) ; as far as i know, gedit is the text editor for gnome, and it's rather long (almost with my computer) to launch a gnome interface in kde (as firefox compared to konqueror)
hope that help

---

### Post by drfalkor on 2005-12-30
Thank you, I installed Kedit - But I couldnt see anything that could set highlight my C++ source files. 
vim ? I'm trying to learn howto use it, but for now - I need something easyer .

---

### Post by jbinc1 on 2005-12-30
How about kwrite or kate?

---

### Post by drfalkor on 2005-12-30
Thank you :p *lets see if I find the highlight button for C++ source files*

---

### Post by asimon on 2005-12-30
Generally Gnome apps take longer to load under KDE because then all the gnome libraries need to be loaded too. If you start the gnome app under gnome most of the libraries are already loaded. The same is true if you load a KDE app under Gnome. That is also sometimes the reason why some Gnome users think that KDE is slow and vice versa.

If you want to edit source code I definitely would go for Kate. You may also want to install the 'kate-plugins' package:
```
 This package contains a variety of useful plugins for Kate, the KDE
 Advanced Text Editor.  These plugins can be loaded through the plugin
 manager in Kate settings.
 .
 Highlights include spell checking, text filtering, HTML/XML construction
 and validation, vim/emacs modeline handling, templates for new files
 and text snippets, opening of C/C++ headers, extraction of C/C++ symbols,
 a tab bar, a Python browser and even more.
```

EDIT: Under Kate the Highlighting function is in the Tools menu under Highlighting. But if you open a C/C++ file it should detect this automatically and highlight by default.

---

### Post by drfalkor on 2005-12-30
Thank you. Gonna try it out later .

---

### Post by yioan on 2005-12-30
I had a similar problem with gedit (gedit and some other gui applications needed more than 3 minutes to run) and the problem on my pc was the loopback adapter. For some reason (pppoeconfig was the reason) the loopback had been disabled from auto start at boot up. Try ifconfig command and notice if the loopback adapter is up.

---

### Post by drfalkor on 2005-12-30
```
falkor@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:DC:1E:56
          inet6 addr: fe80::20c:6eff:fedc:1e56/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:01:03:D5:B6:31
          inet addr:192.168.1.41  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fed5:b631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1011250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:769397228 (733.7 MiB)  TX bytes:124323852 (118.5 MiB)
          Interrupt:17 Base address:0xc000

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:620465 (605.9 KiB)  TX bytes:620465 (605.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.1.39/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1746 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I think I have loopback ? ;)

---

### Post by yioan on 2005-12-30
yes you have. loopback adapter is not the problem in your machine.

---

