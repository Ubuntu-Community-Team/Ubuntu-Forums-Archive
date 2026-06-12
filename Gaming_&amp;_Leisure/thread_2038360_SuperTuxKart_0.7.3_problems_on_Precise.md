---
title: "SuperTuxKart 0.7.3 problems on Precise"
date: 2012-08-06
forum: Gaming &amp; Leisure
---

### Post by giogziro95 on 2012-08-06
My English is not good yet... Sorry for that.
I've Installed SuperTuxKart 0.7.3 on 12.04 via official repository - ppa:stk/daily
The first impression was good but... It's buggy for me :confused:
1. Crash: It always crashes on playtime, on every track I played, except on 'Star Track' - it crashes sometimes (think because of less graphical requirement). I have AMD/ATI Radeon HD 6490M graphics card with official non-opensource driver installed, which often breaks X.org.
```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
```
I tried to run the game in terminal with '--gamepad-debug', here's what I got:
```
gziro@gziro-ProBook:~$ supertuxkart --gamepad-debug
Irrlicht Engine version 1.7.3
Linux 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart'
[FileManager] Addons files will be stored in '/home/gziro/.local/share/supertuxkart/addons'.
[translate] Env var LANGUAGE = 'en_US.UTF-8'
[translate] Env var LANGUAGE = 'en_US.UTF-8', which corresponds to 'English (United States)'
Adding language fallback en
[IrrDriver] Trying OpenGL rendering.
[IrrDriver Temp Logger] Level 2: Unsupported texture format
[IrrDriver Temp Logger] Level 2: Unsupported texture format
Error messages and other text output will be logged to /home/gziro/.config/supertuxkart/stdout.log and /home/gziro/.config/supertuxkart/stderr.log
Bus error (core dumped)
```
Here's stdout.log: [LINK]("http://www.mediafire.com/?q6k63gwcf4rw5pn")
stderr.log file is empty.
2. Graphical bugs: The new character Suzanne and the rescue bird:
[IMG]http://i47.tinypic.com/2dtriue.png[/IMG]
[IMG]http://i47.tinypic.com/23m0tpz.png[/IMG]
Thanks!! :) :P

---

### Post by caffeinatedev on 2012-08-06
I know this sounds really obvious but have you tried using the open-source drivers? Do you have the same problem?

---

### Post by Arthur_D on 2012-08-06
Could you try downloading the official binary here: [http://supertuxkart.net/Downloads](http://supertuxkart.net/Downloads)

Maybe that'll work better; there might be some library mismatch in the PPA (which isn't managed by the core team so not much we can do about it).

---

### Post by giogziro95 on 2012-08-07
Hi,
I through that was caused by AMD proprietary display driver, but I got the same on my other PC with open-source driver for its NVIDIA card and also on Intel Sandybridge graphics. But the game had no problems on Arch. It was clear that it was library mismatch. Thanks Author_D, I installed the game from PlayDeb.net - problem solved! :P

---

### Post by holastickboy on 2012-08-12
Good to see that all was resolved.  Playdeb is a fantastic website, should be included with Ubuntu imo

---

