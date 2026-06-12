---
title: "Inspiron 1525 running too hot"
date: 2008-12-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Checkhovian on 2008-12-18
Hello, I have an Inspiron 1525 currently running 8.04 (came with Vista).

Yesterday I had problems with the laptop spontaneously shutting down on me, and following advice elsewhere on the forums, I added a temperature sensor applet to one of my panels so I could keep an eye on how hot it was getting. And so far the lowest CPU temperature I've seen is 59 C, with it up as high as 73. And I don't consider myself to have been using it hard at all - the most I've had open at once so far today is one word processor window and one firefox window - no gaming or heavy CPU usage...

My cooling fan has yet to kick in that I've heard today... Does this mean the fan is broken? If so, is there anything I can do about that?

---

### Post by llamakc on 2008-12-18
I'm using the same laptop running 8.10 (came w/Vista too). Here's what I do.

My current stats:

```

acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, **47.0 degrees C**
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10

```

So I had tried using gkrellm and the i8kutils package with the gkrellm-i8k plugin, but I was unhappy with it on my desktop. Instead, I added i8kmon to my session startup programs.

In GNOME you can do this by navigating the menu to SYSTEM > PREFERENCES > SESSIONS

Click ADD, name it i8kmon (or whatever you want)

in COMMAND, put** i8kmon -d** [literally put ONLY what I bolded]

add your COMMENT, press SAVE, and checkmark it to start up. You can either logout/login or just start it from a terminal with

```

i8kmon -d &

```

My fan kicks on all of the time.

---

### Post by Checkhovian on 2008-12-18
Does i8kmon actually help control the fan?

---

### Post by llamakc on 2008-12-18
```

ken@ken-laptop 09:06:00:~$ apt-cache show i8kutils
Package: i8kutils
Priority: optional
Section: universe/utils
Installed-Size: 132
Maintainer: Massimo Dal Zotto <dz@debian.org>
Architecture: i386
Version: 1.27
Replaces: i8kfan
Depends: libc6 (>= 2.3.4-1), tk8.4 | wish
Conflicts: i8kfan
Filename: pool/universe/i/i8kutils/i8kutils_1.27_i386.deb
Size: 31448
MD5sum: 98b261bfb74e358c1cbeeb5b1b56efb7
SHA1: 06216cd4fcc8a1e59c9abca698006d7a3f365c7f
SHA256: f7c025e936ec585c98c386b348951b1186c63713bd67a71416d75588f8f87117
Description: utilities for Dell Inspiron and Latitude laptops
 [B]This is a collection of utilities to control Dell Inspiron and Latitude
 laptops. It includes programs to turn the fan on and off, to read fan
 status, CPU temperature, BIOS version and to handle the volume buttons
 and Fn-keys.[/B]
 .
 The package includes also a small Tk applet, designed to be swallowed in the
 gnome panel, which monitors the CPU temperature and controls automatically
 the fans accordingly to user defined thresholds.
 .
 The programs require the kernel module i8k.o which can be compiled from
 the package sources or found in Linux kernel 2.4.14 and later versions.
 The kernel module has been tested only on Inspiron 8000 laptops but it
 should work on any Inspiron and Latitude laptops.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

Yes. `i8kmon -d` puts it in daemon mode, and it will kick the fans on when needed.

---

